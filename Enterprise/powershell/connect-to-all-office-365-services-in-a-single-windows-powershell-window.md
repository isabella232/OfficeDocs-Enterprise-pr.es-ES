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
ms.openlocfilehash: 44f00364d1f81633e06663770f32e0c9f9e99ed8
ms.sourcegitcommit: 22db89d5b13f7d85e03f35f21f25fa288aadf1b4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2018
ms.locfileid: "25575265"
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="da3e9-103">Conectarse a todos los servicios de Office 365 en una sola ventana de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="da3e9-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

 <span data-ttu-id="da3e9-104">**Resumen:** En lugar de administrar los distintos servicios de Office 365 en ventanas independientes de la consola de PowerShell, puede conectarse a todos los servicios de Office 365 y administrarlos desde la ventana de la consola único.</span><span class="sxs-lookup"><span data-stu-id="da3e9-104">**Summary:** Instead of managing different Office 365 services in separate PowerShell console windows, you can connect to all Office 365 services and manage them from single console window.</span></span>
  
<span data-ttu-id="da3e9-p101">Al usar PowerShell para administrar Office 365, es posible tener hasta cinco sesiones diferentes de Windows PowerShell abierto al mismo tiempo correspondiente al centro de administración de Office 365, SharePoint Online, Exchange Online, Skype para profesionales en línea y la seguridad &amp;Centro de cumplimiento. Con cinco métodos de conexión diferentes en las sesiones de Windows PowerShell independientes, su escritorio podría tener este aspecto:</span><span class="sxs-lookup"><span data-stu-id="da3e9-p101">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Office 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, and the Security &amp; Compliance Center. With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![Cinco consolas de Windows PowerShell en ejecución al mismo tiempo](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="da3e9-p102">Esto no es óptima para la administración de Office 365 debido a que no se puede intercambiar datos entre esos cinco windows para la administración de entre-service. En este tema se describe el uso de una sola instancia de Windows PowerShell desde la que puede administrar la seguridad, Skype de negocio en línea, Exchange Online, SharePoint Online y Office 365 &amp; centro de cumplimiento.</span><span class="sxs-lookup"><span data-stu-id="da3e9-p102">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management. This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="da3e9-110">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="da3e9-110">Before you begin</span></span>

<span data-ttu-id="da3e9-111">Antes de poder administrar todo Office 365 desde una sola instancia de Windows PowerShell, tenga en cuenta los siguientes requisitos previos:</span><span class="sxs-lookup"><span data-stu-id="da3e9-111">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="da3e9-p103">Office 365 funciona o escuela cuenta usa para estos procedimientos necesidades para ser un miembro de un rol de administración de Office 365. Para obtener más información, vea [roles de administrador acerca de Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367). Este un requisito para Office 365 PowerShell, no necesariamente para todos los otros servicios de Office 365.</span><span class="sxs-lookup"><span data-stu-id="da3e9-p103">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367). This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="da3e9-115">Puede usar las siguientes versiones de Windows de 64 bits:</span><span class="sxs-lookup"><span data-stu-id="da3e9-115">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="da3e9-116">Windows 10</span><span class="sxs-lookup"><span data-stu-id="da3e9-116">Windows 10</span></span>
    
  - <span data-ttu-id="da3e9-117">Windows 8.1 o Windows 8</span><span class="sxs-lookup"><span data-stu-id="da3e9-117">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="da3e9-118">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="da3e9-118">Windows Server 2019</span></span>
    
  - <span data-ttu-id="da3e9-119">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="da3e9-119">Windows Server 2016</span></span>
    
  - <span data-ttu-id="da3e9-120">Windows Server 2012 R2 o Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="da3e9-120">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="da3e9-121">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="da3e9-121">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="da3e9-122">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="da3e9-122">Windows Server 2008 R2 SP1\*</span></span>
    
    <span data-ttu-id="da3e9-p104">\*Debe instalar Microsoft .NET Framework 4.5. *x* y, a continuación, puede ser el Windows Management Framework 3.0 o Windows Management Framework 4.0. Para obtener más información, vea [instalación de .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) y [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) o [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span><span class="sxs-lookup"><span data-stu-id="da3e9-p104">\* You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0. For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="da3e9-125">Debe usar una versión de 64 bits de Windows debido a los requisitos para la Skype para módulo empresarial en línea y uno de los módulos de Office 365.</span><span class="sxs-lookup"><span data-stu-id="da3e9-125">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="da3e9-126">Debe instalar los módulos que son necesarios para Azure AD, SharePoint Online y Skype para empresarial en línea:</span><span class="sxs-lookup"><span data-stu-id="da3e9-126">You need to install the modules that are required for Azure AD, SharePoint Online, and Skype for Business Online:</span></span>
    
   - [<span data-ttu-id="da3e9-127">V2 de Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="da3e9-127">Azure Active Directory V2</span></span>](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [<span data-ttu-id="da3e9-128">Shell de administración en línea de SharePoint</span><span class="sxs-lookup"><span data-stu-id="da3e9-128">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="da3e9-129">Skype para la empresa en línea, el módulo de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="da3e9-129">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  <span data-ttu-id="da3e9-p105">Windows PowerShell debe configurarse para ejecutar secuencias de comandos firmadas de Skype para profesionales Online, Exchange Online y la seguridad &amp; centro de cumplimiento. Para ello, ejecute el siguiente comando en una sesión de Windows PowerShell con privilegios elevados (una ventana de Windows PowerShell que abra seleccionando **Ejecutar como administrador**).</span><span class="sxs-lookup"><span data-stu-id="da3e9-p105">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center. To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a><span data-ttu-id="da3e9-132">Pasos de conexión cuando se usa una contraseña</span><span class="sxs-lookup"><span data-stu-id="da3e9-132">Connection steps when using a password</span></span>

<span data-ttu-id="da3e9-133">Estos son los pasos para conectarse a todos los servicios en una sola ventana de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="da3e9-133">Here are the steps to connect to all the services in a single PowerShell window.</span></span>
  
1. <span data-ttu-id="da3e9-134">Abra Windows PowerShell como administrador (use **Ejecutar como administrador**).</span><span class="sxs-lookup"><span data-stu-id="da3e9-134">Open Windows PowerShell as an administrator (use **Run as administrator**).</span></span>
    
2. <span data-ttu-id="da3e9-135">Ejecute este comando y especifique su trabajo de Office 365 o escuela las credenciales de cuenta.</span><span class="sxs-lookup"><span data-stu-id="da3e9-135">Run this command, and enter your Office 365 work or school account credentials.</span></span>
    
  ```
  $credential = Get-Credential
  ```

3. <span data-ttu-id="da3e9-136">Ejecute este comando para conectar a Azure Active Directory (AD) con Azure Active Directory PowerShell para el módulo de gráfico.</span><span class="sxs-lookup"><span data-stu-id="da3e9-136">Run this command to connect to Azure Active Directory (AD) using the Azure Active Directory PowerShell for Graph module.</span></span>
    
  ```
   Connect-AzureAD -Credential $credential
  ```
  
  <span data-ttu-id="da3e9-137">Como alternativa, si está utilizando el módulo de Microsoft Azure Active Directory módulo para Windows PowerShell, ejecute este comando.</span><span class="sxs-lookup"><span data-stu-id="da3e9-137">Alternately, if you are using the Microsoft Azure Active Directory Module for Windows PowerShell module, run this command.</span></span>
      
  ```
   Connect-MsolService -Credential $credential
 ```

4. <span data-ttu-id="da3e9-p106">Ejecute estos comandos para conectarse a SharePoint Online. Reemplace _ \<domainhost >_ con el valor real de su dominio. Por ejemplo, para "litwareinc.onmicrosoft.com", la _ \<domainhost >_ valor es "litwareinc".</span><span class="sxs-lookup"><span data-stu-id="da3e9-p106">Run these commands to connect to SharePoint Online. Replace  _\<domainhost>_ with the actual value for your domain. For example, for "litwareinc.onmicrosoft.com", the  _\<domainhost>_ value is "litwareinc".</span></span>
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="da3e9-p107">Ejecute estos comandos para conectarse a Skype para profesionales en línea. Una advertencia sobre el aumento del `WSMan NetworkDelayms` se espera el valor de la primera vez que se conecta y se debe omitir.</span><span class="sxs-lookup"><span data-stu-id="da3e9-p107">Run these commands to connect to Skype for Business Online. A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="da3e9-143">Ejecute estos comandos para conectarse a Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="da3e9-143">Run these commands to connect to Exchange Online.</span></span>
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession
  ```

7. <span data-ttu-id="da3e9-144">Ejecute estos comandos para conectarse a la seguridad &amp; centro de cumplimiento.</span><span class="sxs-lookup"><span data-stu-id="da3e9-144">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

<span data-ttu-id="da3e9-p108">Aquí están todos los comandos en un único bloque cuando se usa Azure Active Directory PowerShell para el módulo de gráfico. Especifique el nombre de host de su dominio y, a continuación, ejecute todas ellas a la vez.</span><span class="sxs-lookup"><span data-stu-id="da3e9-p108">Here are all the commands in a single block when using the Azure Active Directory PowerShell for Graph module. Specify the name of your domain host, and then run them all at one time.</span></span>
  
```
$domainHost="<domain host name, such as litwareinc for litwareinc.onmicrosoft.com>"
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

<span data-ttu-id="da3e9-p109">Como alternativa, aquí están todos los comandos en un único bloque cuando se usa el módulo de Microsoft Azure Active Directory módulo para Windows PowerShell. Especifique el nombre de host de su dominio y, a continuación, ejecute todas ellas a la vez.</span><span class="sxs-lookup"><span data-stu-id="da3e9-p109">Alternately, here are all the commands in a single block when using the Microsoft Azure Active Directory Module for Windows PowerShell module. Specify the name of your domain host, and then run them all at one time.</span></span>
  
```
$domainHost="<domain host name, such as litwareinc for litwareinc.onmicrosoft.com>"
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

<span data-ttu-id="da3e9-149">Cuando esté listo para cerrar la ventana de Windows PowerShell, ejecute este comando para quitar las sesiones activas en Skype para profesionales en línea, Exchange Online, SharePoint Online y la seguridad &amp; centro de cumplimiento:</span><span class="sxs-lookup"><span data-stu-id="da3e9-149">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:</span></span>
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $SccSession ; Disconnect-SPOService
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a><span data-ttu-id="da3e9-150">Pasos de conexión cuando se usa la autenticación multifactor</span><span class="sxs-lookup"><span data-stu-id="da3e9-150">Connection steps when using multi-factor authentication</span></span>

<span data-ttu-id="da3e9-p110">Aquí están todos los comandos en un bloque único para conectarse a Azure AD, SharePoint Online y Skype para negocios con autenticación multifactor en una sola ventana. Especifique el nombre de usuario (UPN) de nombre principal de una cuenta de administrador global y el nombre de host de su dominio y, a continuación, ejecute todas ellas a la vez.</span><span class="sxs-lookup"><span data-stu-id="da3e9-p110">Here are all the commands in a single block to connect to Azure AD, SharePoint Online, and Skype for Buiness using multi-factor authentication in a single window. Specify the user principal name (UPN) name of a global administrator account and your domain host name, and then run them all at one time.</span></span>

````
$acctName="<UPN of a global administrator account>"
$domainHost="<domain host name, such as litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

<span data-ttu-id="da3e9-153">Como alternativa, aquí están todos los comandos cuando se usa el módulo de Microsoft Azure Active Directory módulo para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="da3e9-153">Alternately, here are all the commands when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span>

````
$acctName="<UPN of a global administrator account>"
$domainHost="<domain host name, such as litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

<span data-ttu-id="da3e9-154">Para Exchange Online y la seguridad &amp; centro de cumplimiento, consulte los siguientes temas para conectar con la autenticación multifactor:</span><span class="sxs-lookup"><span data-stu-id="da3e9-154">For Exchange Online and the Security &amp; Compliance Center, see the following topics to connect using multi-factor authentication:</span></span>

- [<span data-ttu-id="da3e9-155">Conectarse a PowerShell para Exchange Online con Multi-Factor Authentication</span><span class="sxs-lookup"><span data-stu-id="da3e9-155">Connect to Exchange Online PowerShell using multi-factor authentication</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell)
- [<span data-ttu-id="da3e9-156">Conectarse a Office 365 seguridad & PowerShell de centro de cumplimiento de normas mediante la autenticación multifactor</span><span class="sxs-lookup"><span data-stu-id="da3e9-156">Connect to Office 365 Security & Compliance Center PowerShell using multi-factor authentication</span></span>](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)
 
<span data-ttu-id="da3e9-157">Tenga en cuenta que en ambos casos, debe conectarse con sesiones separadas de Exchange Online remoto PowerShell del módulo de.</span><span class="sxs-lookup"><span data-stu-id="da3e9-157">Note that in both cases, you must connect using separate sessions of the Exchange Online Remote PowerShell Module.</span></span>


## <a name="see-also"></a><span data-ttu-id="da3e9-158">Vea también</span><span class="sxs-lookup"><span data-stu-id="da3e9-158">See also</span></span>

- [<span data-ttu-id="da3e9-159">Conectarse a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="da3e9-159">Connect to Office 365 PowerShell</span></span>](connect-to-office-365-powershell.md)
- [<span data-ttu-id="da3e9-160">Administrar SharePoint Online con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="da3e9-160">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="da3e9-161">Administrar licencias y cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="da3e9-161">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="da3e9-162">Usar Windows PowerShell para crear informes en Office 365</span><span class="sxs-lookup"><span data-stu-id="da3e9-162">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
