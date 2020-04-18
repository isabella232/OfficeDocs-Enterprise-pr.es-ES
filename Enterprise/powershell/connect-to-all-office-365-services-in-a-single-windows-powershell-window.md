---
title: Conectarse a todos los servicios de Office 365 en una sola ventana de Windows PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: 'Resumen: Conecte Windows PowerShell a todos los servicios de Office 365 en una sola ventana de Windows PowerShell.'
ms.openlocfilehash: d47f4dab4938bd02be25525d2912604f676079db
ms.sourcegitcommit: 58aa8b2e89685490f849e0392d566b7bfb7b933e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2020
ms.locfileid: "43547758"
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a>Conectarse a todos los servicios de Office 365 en una sola ventana de Windows PowerShell

Cuando se usa PowerShell para administrar Office 365, es posible tener hasta cinco sesiones de Windows PowerShell distintas abiertas al mismo tiempo que corresponden a Microsoft 365 centro de administración, SharePoint Online, Exchange Online, Skype empresarial online, Microsoft Teams y el centro de seguridad &amp; y cumplimiento. Con cinco métodos de conexión diferentes en sesiones de Windows PowerShell independientes, el escritorio será similar a este:
  
![Cinco consolas de Windows PowerShell en ejecución al mismo tiempo](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
Esto no es óptimo para la administración de Office 365 porque no puede intercambiar datos entre las cinco ventanas para la administración entre servicios. En este tema se describe cómo usar una única instancia de Windows PowerShell desde la que puede administrar Office 365, Skype empresarial online, Exchange Online, SharePoint Online, Microsoft Teams y el centro &amp; de seguridad y cumplimiento.

>[!Note]
>Actualmente, este artículo solo contiene los comandos para conectarse a la nube de Office 365 Worldwide (+ GCC). Las notas adicionales proporcionan vínculos a artículos con información sobre cómo conectarse a las otras nubes de Office 365.
>

## <a name="before-you-begin"></a>Antes de empezar

Antes de poder administrar todo Office 365 desde una única instancia de Windows PowerShell, tenga en cuenta los siguientes requisitos previos:
  
- La cuenta profesional o educativa de Office 365 que use para estos procedimientos debe ser miembro de un rol de administrador de Office 365. Para obtener más información, vea [Información sobre los roles de administrador de Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367). Este es un requisito para PowerShell de Office 365, no necesariamente para todos los demás servicios de Office 365.
    
- Puede usar las siguientes versiones de Windows de 64 bits:
    
  - Windows 10
    
  - Windows 8.1 o Windows 8
    
  - Windows Server 2019
    
  - Windows Server 2016
    
  - Windows Server 2012 R2 o Windows Server 2012
    
  - Windows 7 Service Pack 1 (SP1)*
    
  - Windows Server 2008 R2 SP1*
    
    \*Debe instalar Microsoft .NET Framework 4,5. *x* y, a continuación, Windows management Framework 3,0 o Windows management Framework 4,0. Para obtener más información, vea [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [windows Management Framework 3,0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4,0](https://go.microsoft.com/fwlink/p/?LinkId=391344).
    
    Debe usar una versión de 64 bits de Windows debido a los requisitos del módulo de Skype empresarial online y uno de los módulos de Office 365.
    
- Debe instalar los módulos necesarios para Azure AD, Exchange Online, SharePoint Online, Skype empresarial online y Teams:
    
   - [Azure Active Directory V2](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [Shell de administración de SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [Skype empresarial online, módulo Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532439)
   - [PowerShell V2 de Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell-v2/exchange-online-powershell-v2?view=exchange-ps#install-and-maintain-the-exchange-online-powershell-v2-module)
   - [Información general sobre PowerShell de Teams](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
    
-  Windows PowerShell tiene que configurarse para ejecutar scripts firmados para Skype empresarial online y &amp; el centro de seguridad y cumplimiento. Para ello, ejecute el siguiente comando en una sesión de Windows PowerShell con privilegios elevados (una ventana de Windows PowerShell que se abre seleccionando **Ejecutar como administrador**).
    
  ```powershell
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a>Pasos de conexión al usar una contraseña

Estos son los pasos para conectarse a todos los servicios en una sola ventana de PowerShell.
  
1. Abra Windows PowerShell.
    
2. Ejecute este comando y escriba sus credenciales de cuenta profesional o educativa de Office 365.
    
  ```powershell
  $credential = Get-Credential
  ```

3. Ejecute este comando para conectarse a Azure Active Directory (AD) con el módulo Azure Active Directory PowerShell para Graph.
    
  ```powershell
  Connect-AzureAD -Credential $credential
  ```
  
  O bien, si usa el módulo Microsoft Azure Active Directory Module para Windows PowerShell, ejecute este comando.
      
  ```powershell
  Connect-MsolService -Credential $credential
 ```

>[!Note]
>PowerShell Core no es compatible con el Módulo Microsoft Azure Active Directory para Windows PowerShell ni los cmdlet que llevan **Msol** en su nombre. Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.
>

4. Ejecute estos comandos para conectarse a SharePoint Online. Reemplace _ \<DomainHost>_ por el valor real de su dominio. Por ejemplo, para "litwareinc.onmicrosoft.com", el valor de la _ \<>DomainHost_ es "litwareinc".
    
  ```powershell
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. Ejecute estos comandos para conectarse a Skype empresarial online. Se espera una advertencia sobre `WSMan NetworkDelayms` el aumento del valor la primera vez que se conecta y debe omitirse.
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. Ejecute este comando para conectarse a Exchange Online.
    
  ```powershell
  Connect-ExchangeOnline -Credential $credential -ShowProgress $true
  ```

>[!Note]
>Para conectarse a Exchange Online para las nubes de Office 365 distintas de todo el mundo, use el parámetro **-ExchangeEnvironmentName** . Consulte [Connect-ExchangeOnline](https://docs.microsoft.com/powershell/module/exchange/powershell-v2-module/connect-exchangeonline?view=exchange-ps) para obtener más información.
>

7. Ejecute estos comandos para conectarse a PowerShell de Microsoft Teams.
    
  ```powershell
  Import-Module MicrosoftTeams
  Connect-MicrosoftTeams -Credential $credential
  ```
  
>[!Note]
>Para conectarse a nubes de Microsoft Teams distintas de todo el mundo, consulte [Connect-Microsoft Teams](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps).
>

8. Ejecute estos comandos para conectarse al centro de &amp; seguridad y cumplimiento.
    
  ```powershell
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
>Para conectarse al centro de &amp; seguridad y cumplimiento para las nubes de Office 365 distintas de todo el mundo, vea [connect to office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).
>

Estos son todos los comandos de un solo bloque cuando se usa el módulo Azure Active Directory PowerShell para Graph. Especifique el nombre de su host de dominio y, a continuación, ejecútelo todos a la vez.
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-AzureAD -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
Connect-ExchangeOnline -Credential $credential -ShowProgress $true
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

Como alternativa, estos son todos los comandos en un solo bloque cuando se usa el módulo Microsoft Azure Active Directory Module para Windows PowerShell. Especifique el nombre de su host de dominio y, a continuación, ejecútelo todos a la vez.
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
Connect-ExchangeOnline -Credential $credential -ShowProgress $true
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

Cuando esté listo para cerrar la ventana de Windows PowerShell, ejecute este comando para quitar las sesiones activas de Skype empresarial online, SharePoint Online, el centro de seguridad &amp; y cumplimiento, y Teams:
  
```powershell
Remove-PSSession $sfboSession ; Remove-PSSession $SccSession ; Disconnect-SPOService ; Disconnect-MicrosoftTeams 
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a>Pasos de conexión al usar la autenticación multifactor

Estos son todos los comandos de un solo bloque para conectarse a Azure AD, SharePoint Online, Skype empresarial, Exchange Online y Teams mediante la autenticación multifactor en una sola ventana mediante el módulo Azure Active Directory PowerShell para Graph. Especifique el nombre principal del usuario (UPN) de una cuenta de usuario y el nombre de host del dominio y, a continuación, ejecútelo todos a la vez.

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
#Exchange Online
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Teams
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```

Como alternativa, estos son todos los comandos al usar el módulo Microsoft Azure Active Directory Module para Windows PowerShell.

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
#Exchange Online
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Teams
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```

Para el centro &amp; de seguridad y cumplimiento, consulte [conectarse a Office 365 Security & cumplimiento del centro de cumplimiento con multi-factor Authentication](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps) para conectarse mediante la autenticación multifactor:

## <a name="see-also"></a>Recursos adicionales

- [Conectarse a PowerShell de Office 365](connect-to-office-365-powershell.md)
- [Administrar SharePoint Online con PowerShell de Office 365](manage-sharepoint-online-with-office-365-powershell.md)
- [Administrar cuentas de usuario, licencias y grupos con Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [Usar Windows PowerShell para crear informes en Office 365](use-windows-powershell-to-create-reports-in-office-365.md)
