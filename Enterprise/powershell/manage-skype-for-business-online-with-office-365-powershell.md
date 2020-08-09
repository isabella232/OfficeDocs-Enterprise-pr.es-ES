---
title: Administrar Skype Empresarial Online con PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 'Resumen: Use PowerShell para Microsoft 365 para administrar las directivas de Skype Empresarial Online, directivas por usuario y opciones de reunión.'
ms.openlocfilehash: 10587dad171c3df9de6985ad314bc1791080b8a1
ms.sourcegitcommit: 839236443410eb804372c4aae969ac9a82ba683b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2020
ms.locfileid: "46592214"
---
# <a name="manage-skype-for-business-online-with-powershell"></a>Administrar Skype Empresarial Online con PowerShell

*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*

Una de las tareas principales de cualquier administrador de Skype Empresarial Online es administrar directivas. Aunque puede realizar algunas de estas tareas en el Centro de administración de Microsoft 365, otras tareas son mucho más rápidas y fáciles en PowerShell. 

## <a name="before-you-start"></a>Antes de comenzar

Descargar e instalar el [módulo de conector de Skype Empresarial Online](https://www.microsoft.com/download/details.aspx?id=39366), y luego reiniciar el equipo.


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a>Conectarse con el nombre y contraseña de una cuenta de administrador de Skype Empresarial Online.

1. Abra el símbolo del sistema de Windows PowerShell y ejecute los siguientes comandos: 
    
   ```powershell
   Import-Module SkypeOnlineConnector
   $userCredential = Get-Credential
   $sfbSession = New-CsOnlineSession -Credential $userCredential
   Import-PSSession $sfbSession
   ```

2. En el cuadro de diálogo **Solicitud de credenciales para Windows PowerShell**, escriba el nombre y la contraseña de su cuenta de administrador de Skype Empresarial Online y, a continuación, haga clic en **Aceptar**.


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multi-factor-authentication"></a>Conectarse con una cuenta de administrador de Skype Empresarial Online mediante la autenticación multifactor.

1. Abra el símbolo del sistema de Windows PowerShell y ejecute los siguientes comandos:

   ```powershell
   Import-Module SkypeOnlineConnector
   $sfbSession = New-CsOnlineSession
   Import-PSSession $sfbSession
   ```

2. Cuando aparezca el comando **New-CsOnlineSession**, escriba el nombre de su cuenta de administrador de Skype Empresarial Online.

3. En el cuadro de diálogo **Iniciar sesión en su cuenta**, escriba la contraseña de administrador de Skype Empresarial Online y, a continuación, haga clic en **Iniciar sesión**.

4. Siga las instrucciones del cuadro de diálogo **Iniciar sesión en su cuenta** para proporcionar información de autenticación adicional, como el código de verificación, y luego haga clic en **Verificar**.

Para obtener más información, consulte los siguientes temas:
  
- [Administrar las directivas de Skype Empresarial Online con PowerShell](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [Asignar directivas a cada usuario de Skype Empresarial Online con PowerShell](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a>Consulte también

[Administrar Microsoft 365 con PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Introducción a PowerShell para Microsoft 365](getting-started-with-office-365-powershell.md)

[Referencias de cmdlet de PowerShell de Skype Empresarial](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

