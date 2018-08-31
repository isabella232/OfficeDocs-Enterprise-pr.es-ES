---
title: Conectarse a todos los servicios de Office 365 en una sola ventana de Windows PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/11/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: 'Resumen: Conectar Windows PowerShell a todos los servicios de Office 365 en una sola ventana de Windows PowerShell.'
ms.openlocfilehash: b4d7b163bfba433196f46046030078c5559c4459
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915835"
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a>Conectarse a todos los servicios de Office 365 en una sola ventana de Windows PowerShell

 **Resumen:** En lugar de administrar los distintos servicios de Office 365 en ventanas independientes de la consola de PowerShell, puede conectarse a todos los servicios de Office 365 y administrarlos desde la ventana de la consola único.
  
Al usar PowerShell para administrar Office 365, es posible tener hasta cinco sesiones diferentes de Windows PowerShell abierto al mismo tiempo correspondiente al centro de administración de Office 365, SharePoint Online, Exchange Online, Skype para profesionales en línea y la seguridad &amp;Centro de cumplimiento. Con cinco métodos de conexión diferentes en las sesiones de Windows PowerShell independientes, su escritorio podría tener este aspecto:
  
![Cinco consolas de Windows PowerShell en ejecución al mismo tiempo](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
Esto no es óptima para la administración de Office 365 debido a que no se puede intercambiar datos entre esos cinco windows para la administración de entre-service. En este tema se describe el uso de una sola instancia de Windows PowerShell desde la que puede administrar la seguridad, Skype de negocio en línea, Exchange Online, SharePoint Online y Office 365 &amp; centro de cumplimiento.

## <a name="before-you-begin"></a>Antes de empezar

Antes de poder administrar todo Office 365 desde una sola instancia de Windows PowerShell, tenga en cuenta los siguientes requisitos previos:
  
- Office 365 funciona o escuela cuenta usa para estos procedimientos necesidades para ser un miembro de un rol de administración de Office 365. Para obtener más información, vea [roles de administrador acerca de Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367). Este un requisito para Office 365 PowerShell, no necesariamente para todos los otros servicios de Office 365.
    
- Puede usar las siguientes versiones de Windows de 64 bits:
    
  - Windows 10
    
  - Windows 8.1 o Windows 8
    
  - Windows Server 2016
    
  - Windows Server 2012 R2 o Windows Server 2012
    
  - Windows 7 Service Pack 1 (SP1)*
    
  - Windows Server 2008 R2 SP1*
    
    \*Debe instalar Microsoft .NET Framework 4.5. *x* y, a continuación, puede ser el Windows Management Framework 3.0 o Windows Management Framework 4.0. Para obtener más información, vea [instalación de .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) y [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) o [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).
    
    Debe usar una versión de 64 bits de Windows debido a los requisitos para la Skype para módulo empresarial en línea y uno de los módulos de Office 365.
    
- Debe instalar los módulos que son necesarios para Azure AD, SharePoint Online y Skype para empresarial en línea:
    
   - [V2 de Azure Active Directory](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [Shell de administración en línea de SharePoint](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [Skype para la empresa en línea, el módulo de Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  Windows PowerShell debe configurarse para ejecutar secuencias de comandos firmadas de Skype para profesionales Online, Exchange Online y la seguridad &amp; centro de cumplimiento. Para ello, ejecute el siguiente comando en una sesión de Windows PowerShell con privilegios elevados (una ventana de Windows PowerShell que abra seleccionando **Ejecutar como administrador**).
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a>Pasos de conexión cuando se usa una contraseña

Estos son los pasos para conectarse a todos los servicios en una sola ventana de PowerShell.
  
1. Abra Windows PowerShell como administrador (use **Ejecutar como administrador**).
    
2. Ejecute este comando y especifique su trabajo de Office 365 o escuela las credenciales de cuenta.
    
  ```
  $credential = Get-Credential
  ```

3. Ejecute este comando para conectar a Azure Active Directory (AD) con Azure Active Directory PowerShell para el módulo de gráfico.
    
  ```
   Connect-AzureAD -Credential $credential
  ```
  
  Como alternativa, si está utilizando el módulo de Microsoft Azure Active Directory módulo para Windows PowerShell, ejecute este comando.
      
  ```
   Connect-MsolService -Credential $credential
 ```

4. Ejecute estos comandos para conectarse a SharePoint Online. Reemplace _ \<domainhost >_ con el valor real de su dominio. Por ejemplo, para "litwareinc.onmicrosoft.com", la _ \<domainhost >_ valor es "litwareinc".
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. Ejecute estos comandos para conectarse a Skype para profesionales en línea. Una advertencia sobre el aumento del `WSMan NetworkDelayms` se espera el valor de la primera vez que se conecta y se debe omitir.
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. Ejecute estos comandos para conectarse a Exchange Online.
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession
  ```

7. Ejecute estos comandos para conectarse a la seguridad &amp; centro de cumplimiento.
    
  ```
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

Aquí están todos los comandos en un único bloque cuando se usa Azure Active Directory PowerShell para el módulo de gráfico. Especifique el nombre de host de su dominio y, a continuación, ejecute todas ellas a la vez.
  
```
$domainHost="<domain host name, such as litware for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-AzureAD -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```

Como alternativa, aquí están todos los comandos en un único bloque cuando se usa el módulo de Microsoft Azure Active Directory módulo para Windows PowerShell. Especifique el nombre de host de su dominio y, a continuación, ejecute todas ellas a la vez.
  
```
$domainHost="<domain host name, such as litware for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```

Cuando esté listo para cerrar la ventana de Windows PowerShell, ejecute este comando para quitar las sesiones activas en Skype para profesionales en línea, Exchange Online, SharePoint Online y la seguridad &amp; centro de cumplimiento:
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $SccSession ; Disconnect-SPOService
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a>Pasos de conexión cuando se usa la autenticación multifactor

Aquí están todos los comandos en un bloque único para conectarse a Azure AD, SharePoint Online y Skype para negocios con autenticación multifactor en una sola ventana. Especifique el nombre de usuario (UPN) de nombre principal de una cuenta de administrador global y el nombre de host de su dominio y, a continuación, ejecute todas ellas a la vez.

````
$acctName="<UPN of a global administrator account>"
$domainHost="<domain host name, such as litware for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

Como alternativa, aquí están todos los comandos cuando se usa el módulo de Microsoft Azure Active Directory módulo para Windows PowerShell.

````
$acctName="<UPN of a global administrator account>"
$domainHost="<domain host name, such as litware for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

Para Exchange Online y la seguridad &amp; centro de cumplimiento, consulte los siguientes temas para conectar con la autenticación multifactor:

- [Conectarse a PowerShell para Exchange Online con Multi-Factor Authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell)
- [Conectarse a Office 365 seguridad & PowerShell de centro de cumplimiento de normas mediante la autenticación multifactor](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)
 
Tenga en cuenta que en ambos casos, debe conectarse con sesiones separadas de Exchange Online remoto PowerShell del módulo de.


## <a name="see-also"></a>Vea también

- [Conectarse a PowerShell de Office 365](connect-to-office-365-powershell.md)
- [Administrar SharePoint Online con PowerShell de Office 365](manage-sharepoint-online-with-office-365-powershell.md)
- [Administrar licencias y cuentas de usuario con PowerShell de Office 365](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [Usar Windows PowerShell para crear informes en Office 365](use-windows-powershell-to-create-reports-in-office-365.md)
