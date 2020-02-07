---
title: Conectarse a todos los servicios de Office 365 en una sola ventana de Windows PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/13/2019
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
ms.openlocfilehash: 91ae87f65e4ef25ab8cba8fcc23c2419cd8bdd73
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844431"
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="4b074-103">Conectarse a todos los servicios de Office 365 en una sola ventana de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4b074-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

<span data-ttu-id="4b074-104">Cuando se usa PowerShell para administrar Office 365, es posible tener hasta cinco sesiones de Windows PowerShell distintas abiertas al mismo tiempo que corresponden a Microsoft 365 centro de administración, SharePoint Online, Exchange Online, Skype empresarial online, Microsoft Teams y el centro de seguridad &amp; y cumplimiento.</span><span class="sxs-lookup"><span data-stu-id="4b074-104">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Microsoft 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, Microsoft Teams, and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="4b074-105">Con cinco métodos de conexión diferentes en sesiones de Windows PowerShell independientes, el escritorio será similar a este:</span><span class="sxs-lookup"><span data-stu-id="4b074-105">With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![Cinco consolas de Windows PowerShell en ejecución al mismo tiempo](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="4b074-107">Esto no es óptimo para la administración de Office 365 porque no puede intercambiar datos entre las cinco ventanas para la administración entre servicios.</span><span class="sxs-lookup"><span data-stu-id="4b074-107">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management.</span></span> <span data-ttu-id="4b074-108">En este tema se describe cómo usar una única instancia de Windows PowerShell desde la que puede administrar Office 365, Skype empresarial online, Exchange Online, SharePoint Online, Microsoft Teams y el centro &amp; de seguridad y cumplimiento.</span><span class="sxs-lookup"><span data-stu-id="4b074-108">This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, Microsoft Teams, and the Security &amp; Compliance Center.</span></span>

>[!Note]
><span data-ttu-id="4b074-109">Actualmente, este artículo solo contiene los comandos para conectarse a la nube de Office 365 Worldwide (+ GCC).</span><span class="sxs-lookup"><span data-stu-id="4b074-109">This article currently only contains the commands to connect to the Office 365 Worldwide (+GCC) cloud.</span></span> <span data-ttu-id="4b074-110">Las notas adicionales proporcionan vínculos a artículos con información sobre cómo conectarse a las otras nubes de Office 365.</span><span class="sxs-lookup"><span data-stu-id="4b074-110">Additional notes provide links to articles with information about connecting to the other Office 365 clouds.</span></span>
>

## <a name="before-you-begin"></a><span data-ttu-id="4b074-111">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="4b074-111">Before you begin</span></span>

<span data-ttu-id="4b074-112">Antes de poder administrar todo Office 365 desde una única instancia de Windows PowerShell, tenga en cuenta los siguientes requisitos previos:</span><span class="sxs-lookup"><span data-stu-id="4b074-112">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="4b074-113">La cuenta profesional o educativa de Office 365 que use para estos procedimientos debe ser miembro de un rol de administrador de Office 365.</span><span class="sxs-lookup"><span data-stu-id="4b074-113">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role.</span></span> <span data-ttu-id="4b074-114">Para obtener más información, vea [Información sobre los roles de administrador de Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="4b074-114">For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span> <span data-ttu-id="4b074-115">Este es un requisito para PowerShell de Office 365, no necesariamente para todos los demás servicios de Office 365.</span><span class="sxs-lookup"><span data-stu-id="4b074-115">This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="4b074-116">Puede usar las siguientes versiones de Windows de 64 bits:</span><span class="sxs-lookup"><span data-stu-id="4b074-116">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="4b074-117">Windows 10</span><span class="sxs-lookup"><span data-stu-id="4b074-117">Windows 10</span></span>
    
  - <span data-ttu-id="4b074-118">Windows 8.1 o Windows 8</span><span class="sxs-lookup"><span data-stu-id="4b074-118">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="4b074-119">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="4b074-119">Windows Server 2019</span></span>
    
  - <span data-ttu-id="4b074-120">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="4b074-120">Windows Server 2016</span></span>
    
  - <span data-ttu-id="4b074-121">Windows Server 2012 R2 o Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="4b074-121">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="4b074-122">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="4b074-122">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="4b074-123">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="4b074-123">Windows Server 2008 R2 SP1\*</span></span>
    
    <span data-ttu-id="4b074-124">\*Debe instalar Microsoft .NET Framework 4,5. *x* y, a continuación, Windows management Framework 3,0 o Windows management Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="4b074-124">\* You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0.</span></span> <span data-ttu-id="4b074-125">Para obtener más información, vea [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [windows Management Framework 3,0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4,0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span><span class="sxs-lookup"><span data-stu-id="4b074-125">For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="4b074-126">Debe usar una versión de 64 bits de Windows debido a los requisitos del módulo de Skype empresarial online y uno de los módulos de Office 365.</span><span class="sxs-lookup"><span data-stu-id="4b074-126">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="4b074-127">Debe instalar los módulos necesarios para Azure AD, SharePoint Online, Skype empresarial online y Teams:</span><span class="sxs-lookup"><span data-stu-id="4b074-127">You need to install the modules that are required for Azure AD, SharePoint Online, Skype for Business Online and Teams:</span></span>
    
   - [<span data-ttu-id="4b074-128">Azure Active Directory V2</span><span class="sxs-lookup"><span data-stu-id="4b074-128">Azure Active Directory V2</span></span>](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [<span data-ttu-id="4b074-129">Shell de administración de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="4b074-129">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="4b074-130">Skype empresarial online, módulo Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4b074-130">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
   - [<span data-ttu-id="4b074-131">Información general sobre PowerShell de Teams</span><span class="sxs-lookup"><span data-stu-id="4b074-131">Teams PowerShell Overview</span></span>](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
    
-  <span data-ttu-id="4b074-132">Windows PowerShell tiene que configurarse para ejecutar scripts firmados para Skype empresarial online, Exchange Online, Microsoft Teams y &amp; el centro de seguridad y cumplimiento.</span><span class="sxs-lookup"><span data-stu-id="4b074-132">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, Microsoft Teams, and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="4b074-133">Para ello, ejecute el siguiente comando en una sesión de Windows PowerShell con privilegios elevados (una ventana de Windows PowerShell que se abre seleccionando **Ejecutar como administrador**).</span><span class="sxs-lookup"><span data-stu-id="4b074-133">To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```powershell
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a><span data-ttu-id="4b074-134">Pasos de conexión al usar una contraseña</span><span class="sxs-lookup"><span data-stu-id="4b074-134">Connection steps when using a password</span></span>

<span data-ttu-id="4b074-135">Estos son los pasos para conectarse a todos los servicios en una sola ventana de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4b074-135">Here are the steps to connect to all the services in a single PowerShell window.</span></span>
  
1. <span data-ttu-id="4b074-136">Abra Windows PowerShell como administrador (use **Ejecutar como administrador**).</span><span class="sxs-lookup"><span data-stu-id="4b074-136">Open Windows PowerShell as an administrator (use **Run as administrator**).</span></span>
    
2. <span data-ttu-id="4b074-137">Ejecute este comando y escriba sus credenciales de la cuenta profesional o educativa de Office 365.</span><span class="sxs-lookup"><span data-stu-id="4b074-137">Run this command, and enter your Office 365 work or school account credentials.</span></span>
    
  ```powershell
  $credential = Get-Credential
  ```

3. <span data-ttu-id="4b074-138">Ejecute este comando para conectarse a Azure Active Directory (AD) con el módulo Azure Active Directory PowerShell para Graph.</span><span class="sxs-lookup"><span data-stu-id="4b074-138">Run this command to connect to Azure Active Directory (AD) using the Azure Active Directory PowerShell for Graph module.</span></span>
    
  ```powershell
  Connect-AzureAD -Credential $credential
  ```
  
  <span data-ttu-id="4b074-139">O bien, si usa el módulo Microsoft Azure Active Directory Module para Windows PowerShell, ejecute este comando.</span><span class="sxs-lookup"><span data-stu-id="4b074-139">Alternately, if you are using the Microsoft Azure Active Directory Module for Windows PowerShell module, run this command.</span></span>
      
  ```powershell
  Connect-MsolService -Credential $credential
 ```

>[!Note]
><span data-ttu-id="4b074-140">PowerShell Core no es compatible con el Módulo Microsoft Azure Active Directory para Windows PowerShell ni los cmdlet que llevan **Msol** en su nombre.</span><span class="sxs-lookup"><span data-stu-id="4b074-140">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="4b074-141">Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4b074-141">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

4. <span data-ttu-id="4b074-142">Ejecute estos comandos para conectarse a SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="4b074-142">Run these commands to connect to SharePoint Online.</span></span> <span data-ttu-id="4b074-143">Reemplace _ \<DomainHost>_ por el valor real de su dominio.</span><span class="sxs-lookup"><span data-stu-id="4b074-143">Replace  _\<domainhost>_ with the actual value for your domain.</span></span> <span data-ttu-id="4b074-144">Por ejemplo, para "litwareinc.onmicrosoft.com", el valor de la _ \<>DomainHost_ es "litwareinc".</span><span class="sxs-lookup"><span data-stu-id="4b074-144">For example, for "litwareinc.onmicrosoft.com", the  _\<domainhost>_ value is "litwareinc".</span></span>
    
  ```powershell
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="4b074-145">Ejecute estos comandos para conectarse a Skype empresarial online.</span><span class="sxs-lookup"><span data-stu-id="4b074-145">Run these commands to connect to Skype for Business Online.</span></span> <span data-ttu-id="4b074-146">Se espera una advertencia sobre `WSMan NetworkDelayms` el aumento del valor la primera vez que se conecta y debe omitirse.</span><span class="sxs-lookup"><span data-stu-id="4b074-146">A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="4b074-147">Ejecute estos comandos para conectarse a Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="4b074-147">Run these commands to connect to Exchange Online.</span></span>
    
  ```powershell
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

>[!Note]
><span data-ttu-id="4b074-148">Para conectarse a Exchange Online para las nubes de Office 365 distintas de todo el mundo, consulte [conectarse a Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span><span class="sxs-lookup"><span data-stu-id="4b074-148">To connect to Exchange Online for Office 365 clouds other than Worldwide, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span>
>

7. <span data-ttu-id="4b074-149">Ejecute estos comandos para conectarse a PowerShell de Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="4b074-149">Run these commands to connect to Teams PowerShell.</span></span>
    
  ```powershell
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
  ```
  
>[!Note]
><span data-ttu-id="4b074-150">Para conectarse a nubes de Microsoft Teams distintas de todo el mundo, consulte [Connect-Microsoft Teams](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps).</span><span class="sxs-lookup"><span data-stu-id="4b074-150">To connect to Microsoft Teams clouds other than Worldwide, see [Connect-MicrosoftTeams](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps).</span></span>
>

8. <span data-ttu-id="4b074-151">Ejecute estos comandos para conectarse al centro de &amp; seguridad y cumplimiento.</span><span class="sxs-lookup"><span data-stu-id="4b074-151">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```powershell
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
><span data-ttu-id="4b074-152">Para conectarse al centro de &amp; seguridad y cumplimiento para las nubes de Office 365 distintas de todo el mundo, vea [connect to office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span><span class="sxs-lookup"><span data-stu-id="4b074-152">To connect to the Security &amp; Compliance Center for Office 365 clouds other than Worldwide, see [Connect to Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span></span>
>

<span data-ttu-id="4b074-153">Estos son todos los comandos de un solo bloque cuando se usa el módulo Azure Active Directory PowerShell para Graph.</span><span class="sxs-lookup"><span data-stu-id="4b074-153">Here are all the commands in a single block when using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="4b074-154">Especifique el nombre de su host de dominio y, a continuación, ejecútelo todos a la vez.</span><span class="sxs-lookup"><span data-stu-id="4b074-154">Specify the name of your domain host, and then run them all at one time.</span></span>
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-AzureAD -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

<span data-ttu-id="4b074-155">Como alternativa, estos son todos los comandos en un solo bloque cuando se usa el módulo Microsoft Azure Active Directory Module para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4b074-155">Alternately, here are all the commands in a single block when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span> <span data-ttu-id="4b074-156">Especifique el nombre de su host de dominio y, a continuación, ejecútelo todos a la vez.</span><span class="sxs-lookup"><span data-stu-id="4b074-156">Specify the name of your domain host, and then run them all at one time.</span></span>
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

<span data-ttu-id="4b074-157">Cuando esté listo para cerrar la ventana de Windows PowerShell, ejecute este comando para quitar las sesiones activas de Skype empresarial online, Exchange Online, SharePoint Online y el centro de seguridad &amp; y cumplimiento:</span><span class="sxs-lookup"><span data-stu-id="4b074-157">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:</span></span>
  
```powershell
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $SccSession ; Disconnect-SPOService ; Disconnect-MicrosoftTeams 
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a><span data-ttu-id="4b074-158">Pasos de conexión al usar la autenticación multifactor</span><span class="sxs-lookup"><span data-stu-id="4b074-158">Connection steps when using multi-factor authentication</span></span>

<span data-ttu-id="4b074-159">Estos son todos los comandos de un solo bloque para conectarse a Azure AD, SharePoint Online y Skype buiness con multi-factor Authentication en una sola ventana usando el módulo Azure Active Directory PowerShell para Graph.</span><span class="sxs-lookup"><span data-stu-id="4b074-159">Here are all the commands in a single block to connect to Azure AD, SharePoint Online, and Skype for Buiness using multi-factor authentication in a single window using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="4b074-160">Especifique el nombre principal del usuario (UPN) de una cuenta de usuario y el nombre de host del dominio y, a continuación, ejecútelo todos a la vez.</span><span class="sxs-lookup"><span data-stu-id="4b074-160">Specify the user principal name (UPN) name of a user account and your domain host name, and then run them all at one time.</span></span>

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
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```

<span data-ttu-id="4b074-161">Como alternativa, estos son todos los comandos al usar el módulo Microsoft Azure Active Directory Module para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4b074-161">Alternately, here are all the commands when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span>

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
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```

<span data-ttu-id="4b074-162">Para Exchange Online y el centro &amp; de seguridad y cumplimiento, vea los siguientes temas para conectarse mediante multi-factor Authentication:</span><span class="sxs-lookup"><span data-stu-id="4b074-162">For Exchange Online and the Security &amp; Compliance Center, see the following topics to connect using multi-factor authentication:</span></span>

- [<span data-ttu-id="4b074-163">Conectarse a PowerShell para Exchange Online con Multi-Factor Authentication</span><span class="sxs-lookup"><span data-stu-id="4b074-163">Connect to Exchange Online PowerShell using multi-factor authentication</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell)
- [<span data-ttu-id="4b074-164">Conectarse a Office 365 Security & el centro de cumplimiento de PowerShell con multi-factor Authentication</span><span class="sxs-lookup"><span data-stu-id="4b074-164">Connect to Office 365 Security & Compliance Center PowerShell using multi-factor authentication</span></span>](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)
 
<span data-ttu-id="4b074-165">Tenga en cuenta que, en ambos casos, debe conectarse usando sesiones independientes del módulo de PowerShell remoto de Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="4b074-165">Note that in both cases, you must connect using separate sessions of the Exchange Online Remote PowerShell Module.</span></span>


## <a name="see-also"></a><span data-ttu-id="4b074-166">Vea también</span><span class="sxs-lookup"><span data-stu-id="4b074-166">See also</span></span>

- [<span data-ttu-id="4b074-167">Conectarse a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="4b074-167">Connect to Office 365 PowerShell</span></span>](connect-to-office-365-powershell.md)
- [<span data-ttu-id="4b074-168">Administrar SharePoint Online con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="4b074-168">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="4b074-169">Administrar cuentas de usuario, licencias y grupos con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="4b074-169">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="4b074-170">Usar Windows PowerShell para crear informes en Office 365</span><span class="sxs-lookup"><span data-stu-id="4b074-170">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
