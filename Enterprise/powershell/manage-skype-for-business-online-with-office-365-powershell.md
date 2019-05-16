---
title: Administrar Skype Empresarial Online con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/13/2018
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 'Resumen: use PowerShell de Office 365 para administrar directivas de Skype Empresarial Online, directivas por usuario y opciones de reunión.'
ms.openlocfilehash: 33c7247686cc8eb308b8db6d4900c89f693004fb
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068736"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a>Administrar Skype Empresarial Online con PowerShell de Office 365

 **Resumen:** use PowerShell de Office 365 para administrar directivas de Skype Empresarial Online, directivas por usuario y opciones de reunión.
  
Una de las tareas principales de cualquier administrador de Skype Empresarial Online es administrar las directivas. Aunque puede realizar algunas de estas tareas en el centro de administración de Office 365, otras tareas son mucho más rápidas y sencillas en PowerShell de Office 365. 

## <a name="before-you-start"></a>Antes de comenzar

Descargue e instale el [módulo de conector de Skype empresarial online](https://www.microsoft.com/en-us/download/details.aspx?id=39366)y, a continuación, reinicie el equipo si se le pide.


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a>Conectarse con el nombre y la contraseña de una cuenta de administrador de Skype empresarial online

1. Abra un símbolo del sistema de Windows PowerShell y ejecute los siguientes comandos: 
    
  ```
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. En el cuadro de diálogo solicitud de credenciales para **Windows PowerShell** , escriba el nombre y la contraseña de la cuenta de administrador en Skype empresarial online y, a continuación, haga clic en **Aceptar**.


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication"></a>Conectarse con una cuenta de administrador de Skype empresarial online con la autenticación multifactor

1. Abra un símbolo del sistema de Windows PowerShell y ejecute los siguientes comandos:

  ```
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. Cuando se lo solicite el comando **New-CsOnlineSession** , escriba el nombre de la cuenta de administrador en Skype empresarial online.

3. En el cuadro de diálogo **iniciar sesión en su cuenta** , escriba su contraseña de administrador en línea de Skype empresarial y, a continuación, haga clic en **iniciar sesión**.

4. Siga las instrucciones del cuadro de diálogo **iniciar sesión en su cuenta** para proporcionar información de autenticación adicional, como un código de comprobación, y haga clic en **comprobar**.

Para obtener más información, consulte los temas siguientes:
  
- [Administrar Skype para políticas de negocios en línea con Office 365 PowerShell](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [Asignar cada usuario Skype para las políticas de negocios en línea con Office 365 PowerShell](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a>Consulte también

[Administrar Office 365 con PowerShell de Office 365](manage-office-365-with-office-365-powershell.md)
  
[Introducción a PowerShell de Office 365](getting-started-with-office-365-powershell.md)

[Referencias de cmdlets de PowerShell de Skype empresarial](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

