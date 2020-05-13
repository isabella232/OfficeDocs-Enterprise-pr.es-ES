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
ms.openlocfilehash: 47fd2be814b446cf12b136e359cdadc9374a7ab6
ms.sourcegitcommit: dce58576a61f2c8efba98657b3f6e277a12a3a7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/12/2020
ms.locfileid: "44208811"
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="5193b-103">Conectarse a todos los servicios de Office 365 en una sola ventana de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5193b-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

<span data-ttu-id="5193b-104">Cuando se usa PowerShell para administrar Office 365, es posible tener hasta cinco sesiones de Windows PowerShell distintas abiertas al mismo tiempo que corresponden a Microsoft 365 centro de administración, SharePoint Online, Exchange Online, Skype empresarial online, Microsoft Teams y el centro de seguridad y &amp; cumplimiento.</span><span class="sxs-lookup"><span data-stu-id="5193b-104">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Microsoft 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, Microsoft Teams, and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="5193b-105">Con cinco métodos de conexión diferentes en sesiones de Windows PowerShell independientes, el escritorio será similar a este:</span><span class="sxs-lookup"><span data-stu-id="5193b-105">With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![Cinco consolas de Windows PowerShell en ejecución al mismo tiempo](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="5193b-107">Esto no es óptimo para la administración de Office 365 porque no puede intercambiar datos entre las cinco ventanas para la administración entre servicios.</span><span class="sxs-lookup"><span data-stu-id="5193b-107">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management.</span></span> <span data-ttu-id="5193b-108">En este tema se describe cómo usar una única instancia de Windows PowerShell desde la que puede administrar Office 365, Skype empresarial online, Exchange Online, SharePoint Online, Microsoft Teams y el centro de seguridad y &amp; cumplimiento.</span><span class="sxs-lookup"><span data-stu-id="5193b-108">This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, Microsoft Teams, and the Security &amp; Compliance Center.</span></span>

>[!Note]
><span data-ttu-id="5193b-109">Actualmente, este artículo solo contiene los comandos para conectarse a la nube de Office 365 Worldwide (+ GCC).</span><span class="sxs-lookup"><span data-stu-id="5193b-109">This article currently only contains the commands to connect to the Office 365 Worldwide (+GCC) cloud.</span></span> <span data-ttu-id="5193b-110">Las notas adicionales proporcionan vínculos a artículos con información sobre cómo conectarse a las otras nubes de Office 365.</span><span class="sxs-lookup"><span data-stu-id="5193b-110">Additional notes provide links to articles with information about connecting to the other Office 365 clouds.</span></span>
>

## <a name="before-you-begin"></a><span data-ttu-id="5193b-111">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="5193b-111">Before you begin</span></span>

<span data-ttu-id="5193b-112">Antes de poder administrar todo Office 365 desde una única instancia de Windows PowerShell, tenga en cuenta los siguientes requisitos previos:</span><span class="sxs-lookup"><span data-stu-id="5193b-112">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="5193b-113">La cuenta profesional o educativa de Office 365 que use para estos procedimientos debe ser miembro de un rol de administrador de Office 365.</span><span class="sxs-lookup"><span data-stu-id="5193b-113">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role.</span></span> <span data-ttu-id="5193b-114">Para obtener más información, vea [Información sobre los roles de administrador de Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="5193b-114">For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span> <span data-ttu-id="5193b-115">Este es un requisito para PowerShell de Office 365, no necesariamente para todos los demás servicios de Office 365.</span><span class="sxs-lookup"><span data-stu-id="5193b-115">This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="5193b-116">Puede usar las siguientes versiones de Windows de 64 bits:</span><span class="sxs-lookup"><span data-stu-id="5193b-116">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="5193b-117">Windows 10</span><span class="sxs-lookup"><span data-stu-id="5193b-117">Windows 10</span></span>
    
  - <span data-ttu-id="5193b-118">Windows 8.1 o Windows 8</span><span class="sxs-lookup"><span data-stu-id="5193b-118">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="5193b-119">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="5193b-119">Windows Server 2019</span></span>
    
  - <span data-ttu-id="5193b-120">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="5193b-120">Windows Server 2016</span></span>
    
  - <span data-ttu-id="5193b-121">Windows Server 2012 R2 o Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="5193b-121">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="5193b-122">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="5193b-122">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="5193b-123">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="5193b-123">Windows Server 2008 R2 SP1\*</span></span>
    
    <span data-ttu-id="5193b-124">\*Debe instalar Microsoft .NET Framework 4,5. *x* y, a continuación, Windows management Framework 3,0 o Windows management Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="5193b-124">\* You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0.</span></span> <span data-ttu-id="5193b-125">Para obtener más información, vea [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [windows Management Framework 3,0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4,0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span><span class="sxs-lookup"><span data-stu-id="5193b-125">For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="5193b-126">Debe usar una versión de 64 bits de Windows debido a los requisitos del módulo de Skype empresarial online y uno de los módulos de Office 365.</span><span class="sxs-lookup"><span data-stu-id="5193b-126">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="5193b-127">Debe instalar los módulos necesarios para Azure Active Directory (Azure AD), Exchange Online, SharePoint Online, Skype empresarial online y Teams:</span><span class="sxs-lookup"><span data-stu-id="5193b-127">You need to install the modules that are required for Azure Active Directory (Azure AD), Exchange Online, SharePoint Online, Skype for Business Online and Teams:</span></span>
    
   - [<span data-ttu-id="5193b-128">Azure Active Directory V2</span><span class="sxs-lookup"><span data-stu-id="5193b-128">Azure Active Directory V2</span></span>](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [<span data-ttu-id="5193b-129">Shell de administración de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5193b-129">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="5193b-130">Skype empresarial online, módulo Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5193b-130">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
   - [<span data-ttu-id="5193b-131">PowerShell V2 de Exchange Online</span><span class="sxs-lookup"><span data-stu-id="5193b-131">Exchange Online PowerShell V2</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell-v2/exchange-online-powershell-v2?view=exchange-ps#install-and-maintain-the-exchange-online-powershell-v2-module)
   - [<span data-ttu-id="5193b-132">Información general sobre PowerShell de Teams</span><span class="sxs-lookup"><span data-stu-id="5193b-132">Teams PowerShell Overview</span></span>](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
    
-  <span data-ttu-id="5193b-133">Windows PowerShell tiene que configurarse para ejecutar scripts firmados para Skype empresarial online y el centro de seguridad y &amp; cumplimiento.</span><span class="sxs-lookup"><span data-stu-id="5193b-133">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="5193b-134">Para ello, ejecute el siguiente comando en una sesión de Windows PowerShell con privilegios elevados (una ventana de Windows PowerShell que se abre seleccionando **Ejecutar como administrador**).</span><span class="sxs-lookup"><span data-stu-id="5193b-134">To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```powershell
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a><span data-ttu-id="5193b-135">Pasos de conexión al usar una contraseña</span><span class="sxs-lookup"><span data-stu-id="5193b-135">Connection steps when using a password</span></span>

<span data-ttu-id="5193b-136">Estos son los pasos para conectarse a todos los servicios en una sola ventana de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5193b-136">Here are the steps to connect to all the services in a single PowerShell window.</span></span>
  
1. <span data-ttu-id="5193b-137">Abra Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5193b-137">Open Windows PowerShell.</span></span>
    
2. <span data-ttu-id="5193b-138">Ejecute este comando y escriba sus credenciales de cuenta profesional o educativa de Office 365.</span><span class="sxs-lookup"><span data-stu-id="5193b-138">Run this command and enter your Office 365 work or school account credentials.</span></span>
    
  ```powershell
  $credential = Get-Credential
  ```

3. <span data-ttu-id="5193b-139">Ejecute este comando para conectarse a Azure AD con el módulo Azure Active Directory PowerShell para Graph.</span><span class="sxs-lookup"><span data-stu-id="5193b-139">Run this command to connect to Azure AD using the Azure Active Directory PowerShell for Graph module.</span></span>
    
  ```powershell
  Connect-AzureAD -Credential $credential
  ```
  
  <span data-ttu-id="5193b-140">O bien, si usa el módulo Microsoft Azure Active Directory Module para Windows PowerShell, ejecute este comando.</span><span class="sxs-lookup"><span data-stu-id="5193b-140">Alternately, if you are using the Microsoft Azure Active Directory Module for Windows PowerShell module, run this command.</span></span>
      
  ```powershell
  Connect-MsolService -Credential $credential
 ```

>[!Note]
><span data-ttu-id="5193b-141">PowerShell Core no es compatible con el Módulo Microsoft Azure Active Directory para Windows PowerShell ni los cmdlet que llevan **Msol** en su nombre.</span><span class="sxs-lookup"><span data-stu-id="5193b-141">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="5193b-142">Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5193b-142">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

4. <span data-ttu-id="5193b-143">Ejecute estos comandos para conectarse a SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="5193b-143">Run these commands to connect to SharePoint Online.</span></span> <span data-ttu-id="5193b-144">Reemplace _ \< DomainHost>_ por el valor real de su dominio.</span><span class="sxs-lookup"><span data-stu-id="5193b-144">Replace  _\<domainhost>_ with the actual value for your domain.</span></span> <span data-ttu-id="5193b-145">Por ejemplo, para "litwareinc.onmicrosoft.com", el valor de la _ \<>DomainHost_ es "litwareinc".</span><span class="sxs-lookup"><span data-stu-id="5193b-145">For example, for "litwareinc.onmicrosoft.com", the  _\<domainhost>_ value is "litwareinc".</span></span>
    
  ```powershell
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="5193b-146">Ejecute estos comandos para conectarse a Skype empresarial online.</span><span class="sxs-lookup"><span data-stu-id="5193b-146">Run these commands to connect to Skype for Business Online.</span></span> <span data-ttu-id="5193b-147">Se espera una advertencia sobre el aumento del `WSMan NetworkDelayms` valor la primera vez que se conecta y debe omitirse.</span><span class="sxs-lookup"><span data-stu-id="5193b-147">A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="5193b-148">Ejecute este comando para conectarse a Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="5193b-148">Run this command to connect to Exchange Online.</span></span>
    
  ```powershell
  Connect-ExchangeOnline -Credential $credential -ShowProgress $true
  ```

>[!Note]
><span data-ttu-id="5193b-149">Para conectarse a Exchange Online para las nubes de Office 365 distintas de todo el mundo, use el parámetro **-ExchangeEnvironmentName** .</span><span class="sxs-lookup"><span data-stu-id="5193b-149">To connect to Exchange Online for Office 365 clouds other than Worldwide, use the **-ExchangeEnvironmentName** parameter.</span></span> <span data-ttu-id="5193b-150">Consulte [Connect-ExchangeOnline](https://docs.microsoft.com/powershell/module/exchange/powershell-v2-module/connect-exchangeonline?view=exchange-ps) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="5193b-150">See [Connect-ExchangeOnline](https://docs.microsoft.com/powershell/module/exchange/powershell-v2-module/connect-exchangeonline?view=exchange-ps) for more information.</span></span>
>

7. <span data-ttu-id="5193b-151">Ejecute estos comandos para conectarse a PowerShell de Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="5193b-151">Run these commands to connect to Teams PowerShell.</span></span>
    
  ```powershell
  Import-Module MicrosoftTeams
  Connect-MicrosoftTeams -Credential $credential
  ```
  
>[!Note]
><span data-ttu-id="5193b-152">Para conectarse a nubes de Microsoft Teams distintas de todo el mundo, consulte [Connect-Microsoft Teams](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps).</span><span class="sxs-lookup"><span data-stu-id="5193b-152">To connect to Microsoft Teams clouds other than Worldwide, see [Connect-MicrosoftTeams](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps).</span></span>
>

8. <span data-ttu-id="5193b-153">Ejecute estos comandos para conectarse al centro de seguridad y &amp; cumplimiento.</span><span class="sxs-lookup"><span data-stu-id="5193b-153">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```powershell
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
><span data-ttu-id="5193b-154">Para conectarse al &amp; centro de seguridad y cumplimiento para las nubes de office 365 distintas de todo el mundo, vea [Connect to Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span><span class="sxs-lookup"><span data-stu-id="5193b-154">To connect to the Security &amp; Compliance Center for Office 365 clouds other than Worldwide, see [Connect to Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span></span>
>

<span data-ttu-id="5193b-155">Estos son todos los comandos de un solo bloque cuando se usa el módulo Azure Active Directory PowerShell para Graph.</span><span class="sxs-lookup"><span data-stu-id="5193b-155">Here are all the commands in a single block when using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="5193b-156">Especifique el nombre de su host de dominio y, a continuación, ejecútelo todos a la vez.</span><span class="sxs-lookup"><span data-stu-id="5193b-156">Specify the name of your domain host, and then run them all at one time.</span></span>
  
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

<span data-ttu-id="5193b-157">Como alternativa, estos son todos los comandos en un solo bloque cuando se usa el módulo Microsoft Azure Active Directory Module para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5193b-157">Alternately, here are all the commands in a single block when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span> <span data-ttu-id="5193b-158">Especifique el nombre de su host de dominio y, a continuación, ejecútelo todos a la vez.</span><span class="sxs-lookup"><span data-stu-id="5193b-158">Specify the name of your domain host, and then run them all at one time.</span></span>
  
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

<span data-ttu-id="5193b-159">Cuando esté listo para cerrar la ventana de Windows PowerShell, ejecute este comando para quitar las sesiones activas de Skype empresarial online, SharePoint Online, el centro de seguridad &amp; y cumplimiento, y Teams:</span><span class="sxs-lookup"><span data-stu-id="5193b-159">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, SharePoint Online, the Security &amp; Compliance Center, and Teams:</span></span>
  
```powershell
Remove-PSSession $sfboSession ; Remove-PSSession $SccSession ; Disconnect-SPOService ; Disconnect-MicrosoftTeams 
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a><span data-ttu-id="5193b-160">Pasos de conexión al usar la autenticación multifactor</span><span class="sxs-lookup"><span data-stu-id="5193b-160">Connection steps when using multi-factor authentication</span></span>

<span data-ttu-id="5193b-161">Estos son todos los comandos de un solo bloque para conectarse a Azure AD, SharePoint Online, Skype empresarial, Exchange Online y Teams mediante la autenticación multifactor en una sola ventana mediante el módulo Azure Active Directory PowerShell para Graph.</span><span class="sxs-lookup"><span data-stu-id="5193b-161">Here are all the commands in a single block to connect to Azure AD, SharePoint Online, Skype for Business, Exchange Online, and Teams using multi-factor authentication in a single window using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="5193b-162">Especifique el nombre principal del usuario (UPN) de una cuenta de usuario y el nombre de host del dominio y, a continuación, ejecútelo todos a la vez.</span><span class="sxs-lookup"><span data-stu-id="5193b-162">Specify the user principal name (UPN) name of a user account and your domain host name, and then run them all at one time.</span></span>

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

<span data-ttu-id="5193b-163">Como alternativa, estos son todos los comandos al usar el módulo Microsoft Azure Active Directory Module para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5193b-163">Alternately, here are all the commands when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span>

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

<span data-ttu-id="5193b-164">Para el centro de seguridad &amp; y cumplimiento, consulte [conectarse a Office 365 Security & cumplimiento del centro de cumplimiento con multi-factor Authentication](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps) para conectarse mediante la autenticación multifactor:</span><span class="sxs-lookup"><span data-stu-id="5193b-164">For the Security &amp; Compliance Center, see [Connect to Office 365 Security & Compliance Center PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps) to connect using multi-factor authentication:</span></span>

## <a name="see-also"></a><span data-ttu-id="5193b-165">Vea también</span><span class="sxs-lookup"><span data-stu-id="5193b-165">See also</span></span>

- [<span data-ttu-id="5193b-166">Conectarse a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="5193b-166">Connect to Office 365 PowerShell</span></span>](connect-to-office-365-powershell.md)
- [<span data-ttu-id="5193b-167">Administrar SharePoint Online con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="5193b-167">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="5193b-168">Administrar cuentas de usuario, licencias y grupos con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="5193b-168">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="5193b-169">Usar Windows PowerShell para crear informes en Office 365</span><span class="sxs-lookup"><span data-stu-id="5193b-169">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
