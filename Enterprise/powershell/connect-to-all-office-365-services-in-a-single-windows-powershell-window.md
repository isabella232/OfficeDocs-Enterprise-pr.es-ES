---
title: Conectarse a todos los servicios de Microsoft 365 en una sola ventana de Windows PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/10/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: 'Resumen: Conectar Windows PowerShell a todos los servicios de Microsoft 365 en una sola ventana de Windows PowerShell'
ms.openlocfilehash: de6bb592233b44a14848b1512230197bb8eb75fb
ms.sourcegitcommit: 1aaa4c6d10eb14f4b3d5a452f2e64c96f5d96ae4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "46560065"
---
# <a name="connect-to-all-microsoft-365-services-in-a-single-windows-powershell-window"></a>Conectarse a todos los servicios de Microsoft 365 en una sola ventana de Windows PowerShell

Cuando usa PowerShell para administrar Microsoft 365, es posible tener hasta cinco sesiones de Windows PowerShell distintas abiertas al mismo tiempo, que corresponden al Centro de administración de Microsoft 365, SharePoint Online, Exchange Online, Skype Empresarial Online, Microsoft Teams y el Centro de cumplimiento &amp; seguridad. Con cinco métodos de conexión distintos en sesiones diversas de Windows PowerShell, el escritorio podría tener este aspecto:
  
![Cinco consolas de Windows PowerShell en ejecución al mismo tiempo](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
Esto no es ideal para la administración de Microsoft 365 porque no podemos intercambiar datos entre esas cinco ventanas para la administración entre servicios. Este tema describe cómo usar una única instancia de Windows PowerShell desde la que administrar cuentas de Microsoft 365, SharePoint Online, Exchange Online, Skype Empresarial Online, Microsoft Teams y el Centro de cumplimiento &amp; seguridad.

>[!Note]
>Actualmente, este artículo solo contiene los comandos para conectarse a la nube mundial (+GCC). En las notas adicionales tiene vínculos a artículos que explican cómo conectarse a otras nubes de Microsoft 365.
>

## <a name="before-you-begin"></a>Antes de empezar

Antes de poder administrar todo Microsoft 365 desde una sola instancia de Windows PowerShell, tenga en cuenta los siguientes requisitos previos:
  
- La cuenta profesional o educativa de Microsoft 365 que use para estos procedimientos tiene que ser un miembro del rol de administrador de Microsoft 365. Para obtener más información, vea [Asignar roles de administrador](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide). Este es un requisito de PowerShell para Microsoft 365, no necesariamente para todos los demás servicios de Microsoft 365.
    
- Puede usar las siguientes versiones de Windows de 64 bits:
    
  - Windows 10
    
  - Windows 8.1 o Windows 8
    
  - Windows Server 2019
    
  - Windows Server 2016
    
  - Windows Server 2012 R2 o Windows Server 2012
    
  - Windows 7 Service Pack 1 (SP1)*
    
  - Windows Server 2008 R2 SP1*
    
    \* Es necesario instalar Microsoft .NET Framework 4.5.*x* y, luego, Windows Management Framework 3.0 o Windows Management Framework 4.0. Para más información, consulte [Instalación de .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) y [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) o [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).
    
    Debe usar una versión de 64 bits de Windows para cumplir los requisitos del módulo Skype Empresarial Online y uno de los módulos de Microsoft 365.
    
- Debe instalar los módulos necesarios para Azure Active Directory (Azure AD), Exchange Online, SharePoint Online, Skype Empresarial Online y Teams:
    
   - [Azure Active Directory V2](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [Shell de administración de SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [Skype Empresarial Online, módulo de Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532439)
   - [Exchange Online PowerShell V2](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell-v2/exchange-online-powershell-v2?view=exchange-ps#install-and-maintain-the-exchange-online-powershell-v2-module)
   - [Descripción de PowerShell para Teams](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
    
-  Windows PowerShell necesita configurarse para ejecutar scripts firmados en Skype Empresarial Online y en el Centro de seguridad &amp; cumplimiento. Para ello, ejecute el siguiente comando en una sesión de Windows PowerShell con permisos elevados (es decir, una ventana de Windows PowerShell que se abre seleccionando **Ejecutar como administrador**):
    
   ```powershell
   Set-ExecutionPolicy RemoteSigned
   ```

## <a name="connection-steps-when-using-just-a-password"></a>Pasos de conexión al usar solo una contraseña

Estos son los pasos para conectarse a todos los servicios en una única ventana de PowerShell cuando se usa solo una contraseña para iniciar sesión.
  
1. Abra Windows PowerShell.
    
2. Ejecute este comando y escriba las credenciales de su cuenta profesional o educativa de Microsoft 365.
    
   ```powershell
   $credential = Get-Credential
   ```

3. Ejecute este comando para conectarse a Azure AD con el módulo Azure Active Directory PowerShell para Graph.
    
   ```powershell
   Connect-AzureAD -Credential $credential
   ```
  
   Si usa el Módulo Microsoft Azure Active Directory para Windows PowerShell, también puede ejecutar este comando.
      
   ```powershell
   Connect-MsolService -Credential $credential
   ```

   > [!Note]
   > PowerShell Core no es compatible con el Módulo Microsoft Azure Active Directory para Windows PowerShell ni los cmdlet que llevan **Msol** en su nombre. Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.

4. Ejecute estos comandos para conectarse a SharePoint Online. Especifique el nombre de la organización para su dominio. Por ejemplo, para "litwareinc.onmicrosoft.com", el valor del nombre de la organización es "litwareinc".
    
   ```powershell
   $orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
   Connect-SPOService -Url https://$orgName-admin.sharepoint.com -Credential $userCredential
   ```

5. Ejecute estos comandos para conectarse a Skype Empresarial Online. La primera vez que se conecte, verá una advertencia sobre el aumento del valor `WSMan NetworkDelayms` que debe omitir.
     
   ```powershell
   Import-Module SkypeOnlineConnector
   $sfboSession = New-CsOnlineSession -Credential $credential
   Import-PSSession $sfboSession
   ```

6. Ejecute este comando para conectarse a Exchange Online.
    
   ```powershell
   Connect-ExchangeOnline -Credential $credential -ShowProgress $true
   ```

   > [!Note]
   > Para conectarse a Exchange Online para las nubes de Microsoft 365 que no sean mundiales, use el parámetro **-ExchangeEnvironmentName**. Para obtener más información, consulte [Connect-ExchangeOnline](https://docs.microsoft.com/powershell/module/exchange/powershell-v2-module/connect-exchangeonline?view=exchange-ps).

7. Ejecute estos comandos para conectarse a Teams PowerShell.
    
   ```powershell
   Import-Module MicrosoftTeams
   Connect-MicrosoftTeams -Credential $credential
   ```
  
   > [!Note]
   > Para conectarse a nubes de Microsoft Teams que no sean mundiales, consulte [Connect-MicrosoftTeams](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps).

8. Ejecute estos comandos para conectarse al Centro de seguridad &amp; cumplimiento.
    
   ```powershell
   $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
   Import-PSSession $SccSession -Prefix cc
   ```

   > [!Note]
   > Para conectarse al Centro de seguridad &amp; cumplimiento para nubes de Microsoft 365 que no sean mundiales, vea [Conectar con el Centro de seguridad y cumplimiento de PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).

Aquí tiene todos los comandos en un único bloque cuando se usa el módulo Azure Active Directory PowerShell para Graph. Especifique el nombre del host de su dominio y, a continuación, ejecútelos todos a la vez.
  
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

Como alternativa, estos son todos los comandos en un único bloque cuando se usa el Módulo Microsoft Azure Active Directory para Windows PowerShell. Especifique el nombre del host de su dominio y, a continuación, ejecútelos todos a la vez.
  
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

Cuando esté listo para cerrar la ventana de Windows PowerShell, ejecute este comando para quitar las sesiones activas de Skype Empresarial Online, SharePoint Online, el Centro de seguridad &amp; cumplimiento y Teams:
  
```powershell
Remove-PSSession $sfboSession ; Remove-PSSession $SccSession ; Disconnect-SPOService ; Disconnect-MicrosoftTeams 
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a>Pasos de conexión al usar autenticación multifactor

Estos son todos los comandos de un único bloque para conectarse a Azure AD, SharePoint Online, Skype Empresarial, Exchange Online y Teams mediante la autenticación multifactor en una única ventana con el módulo Azure Active Directory PowerShell para Graph. Especifique el nombre de usuario principal (UPN) de una cuenta de usuario y el nombre de host del dominio y, a continuación, ejecútelos todos al mismo tiempo.

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

Como alternativa, estos son todos los comandos cuando use el Módulo Microsoft Azure Active Directory para Windows PowerShell.

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

Para obtener más datos sobre el Centro de seguridad &amp; cumplimiento, vea [Conectarse al Centro de seguridad y cumplimiento de PowerShell con la autenticación multifactor](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps) para conectarse mediante la autenticación multifactor:

## <a name="see-also"></a>Recursos adicionales

- [Conectarse a Microsoft 365 con PowerShell](connect-to-office-365-powershell.md)
- [Administrar SharePoint Online con PowerShell](manage-sharepoint-online-with-office-365-powershell.md)
- [Administrar cuentas de usuario, licencias y grupos de Microsoft 365 con PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [Usar Windows PowerShell para crear informes en Microsoft 365](use-windows-powershell-to-create-reports-in-office-365.md)
