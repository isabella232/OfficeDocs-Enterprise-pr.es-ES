---
title: Administrar Skype empresarial online con PowerShell
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
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 'Resumen: Use PowerShell para Microsoft 365 para administrar directivas de Skype empresarial online, directivas por usuario y opciones de reunión.'
ms.openlocfilehash: 0701fdb8a0a1f588e1c113ad7050ed516638aebc
ms.sourcegitcommit: d9abb99b336170f07b8f3f6d00fac19ad2159d3a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/28/2020
ms.locfileid: "46502615"
---
# <a name="manage-skype-for-business-online-with-powershell"></a>Administrar Skype empresarial online con PowerShell

*Este artículo afecta tanto a Office 365 Enterprise como a Microsoft 365 Enterprise*

Una de las tareas principales de cualquier administrador de Skype Empresarial Online es administrar las directivas. Aunque puede llevar a cabo algunas de estas tareas en el centro de administración de 365 de Microsoft, otras tareas son mucho más rápidas y fáciles en PowerShell. 

## <a name="before-you-start"></a>Antes de comenzar

Descargue e instale el [módulo de conector de Skype empresarial online](https://www.microsoft.com/download/details.aspx?id=39366)y, a continuación, reinicie el equipo.


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a>Conectarse con el nombre y la contraseña de una cuenta de administrador de Skype empresarial online

1. Abra un símbolo del sistema de Windows PowerShell y ejecute los siguientes comandos: 
    
   ```powershell
   Import-Module SkypeOnlineConnector
   $userCredential = Get-Credential
   $sfbSession = New-CsOnlineSession -Credential $userCredential
   Import-PSSession $sfbSession
   ```

2. En el cuadro de diálogo **solicitud de credenciales para Windows PowerShell** , escriba el nombre y la contraseña de la cuenta de administrador en Skype empresarial online y, a continuación, haga clic en **Aceptar**.


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multi-factor-authentication"></a>Conectarse con una cuenta de administrador de Skype empresarial online con autenticación multifactor

1. Abra un símbolo del sistema de Windows PowerShell y ejecute los siguientes comandos:

   ```powershell
   Import-Module SkypeOnlineConnector
   $sfbSession = New-CsOnlineSession
   Import-PSSession $sfbSession
   ```

2. Cuando se lo solicite el comando **New-CsOnlineSession** , escriba el nombre de la cuenta de administrador en Skype empresarial online.

3. En el cuadro de diálogo **iniciar sesión en su cuenta** , escriba su contraseña de administrador en línea de Skype empresarial y, a continuación, haga clic en **iniciar sesión**.

4. Siga las instrucciones del cuadro de diálogo **iniciar sesión en su cuenta** para proporcionar información de autenticación adicional, como un código de comprobación, y haga clic en **comprobar**.

Para obtener más información, vea los siguientes temas:
  
- [Administrar directivas de Skype empresarial online con PowerShell](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [Asignar directivas de Skype empresarial online por usuario con PowerShell](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a>Consulte también

[Administrar Microsoft 365 con PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Introducción a PowerShell para Microsoft 365](getting-started-with-office-365-powershell.md)

[Referencias de cmdlets de PowerShell de Skype empresarial](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

