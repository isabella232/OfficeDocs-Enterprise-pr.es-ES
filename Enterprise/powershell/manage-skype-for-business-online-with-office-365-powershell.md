---
title: Administrar Skype Empresarial Online con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/22/2018
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 'Resumen: use PowerShell de Office 365 para administrar directivas de Skype Empresarial Online, directivas por usuario y opciones de reunión.'
ms.openlocfilehash: f490131491a026961b0a5db312df5780483eadd9
ms.sourcegitcommit: b39b8ae3b4268d6475b54e2fdb62982b2c7d9943
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/12/2018
ms.locfileid: "20319241"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a>Administrar Skype Empresarial Online con PowerShell de Office 365

 **Resumen:** use PowerShell de Office 365 para administrar directivas de Skype Empresarial Online, directivas por usuario y opciones de reunión.
  
Es una de las tareas principales de cualquier Skype administrador empresarial en línea de administración de directivas. Aunque puede realizar algunas de estas tareas en el centro de administración de Office 365, otras tareas son mucho más rápido y sencillo en PowerShell de Office 365. 

## <a name="before-you-start"></a>Antes de comenzar

Descargar e instalar el [Skype para el módulo del conector en línea de negocio](https://www.microsoft.com/en-us/download/details.aspx?id=39366)y, a continuación, reinicie el equipo si se le solicita.


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a>Conectar utilizando un Skype para el nombre de cuenta de administrador empresarial en línea y la contraseña

1. Abra un símbolo del sistema de Windows PowerShell y ejecute los siguientes comandos: 
    
  ```
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. En el cuadro de diálogo **Solicitud de credenciales de Windows PowerShell** , escriba su Skype para el nombre de la cuenta de administrador empresarial en línea y la contraseña y, a continuación, haga clic en **Aceptar**.


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication"></a>Conectar con un Skype para la cuenta de administrador empresarial en línea con la autenticación multifactor

1. Abra un símbolo del sistema de Windows PowerShell y ejecute los siguientes comandos:

  ```
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. Cuando se le solicite el comando **New-CsOnlineSession** , escriba su Skype para el nombre de la cuenta de administrador empresarial en línea.

3. En el cuadro de diálogo **iniciar sesión en su cuenta** , escriba su Skype para contraseña de administrador empresarial en línea y, a continuación, haga clic en **iniciar sesión**.

4. Siga las instrucciones que aparecen en el cuadro de diálogo **iniciar sesión en su cuenta** para proporcionar información de autenticación adicionales, como un código de comprobación y, a continuación, haga clic en **Comprobar**.

Para obtener más información, vea los temas siguientes:
  
- [Administrar Skype para políticas de negocios en línea con Office 365 PowerShell](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [Asignar cada usuario Skype para las políticas de negocios en línea con Office 365 PowerShell](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a>Consulte también

[Administrar Office 365 con PowerShell de Office 365](manage-office-365-with-office-365-powershell.md)
  
[Introducción a PowerShell de Office 365](getting-started-with-office-365-powershell.md)

