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
ms.openlocfilehash: 222355bb3c8c9d8123fd2738c80a7225da15ca46
ms.sourcegitcommit: d9abb99b336170f07b8f3f6d00fac19ad2159d3a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/28/2020
ms.locfileid: "46502685"
---
# <a name="connect-to-all-microsoft-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="77a13-103">Conectarse a todos los servicios de Microsoft 365 en una sola ventana de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="77a13-103">Connect to all Microsoft 365 services in a single Windows PowerShell window</span></span>

<span data-ttu-id="77a13-104">Cuando usa PowerShell para administrar Microsoft 365, es posible tener hasta cinco sesiones de Windows PowerShell distintas abiertas al mismo tiempo, que corresponden al Centro de administración de Microsoft 365, SharePoint Online, Exchange Online, Skype Empresarial Online, Microsoft Teams y el Centro de cumplimiento &amp; seguridad.</span><span class="sxs-lookup"><span data-stu-id="77a13-104">When you use PowerShell to manage Microsoft 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Microsoft 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, Microsoft Teams, and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="77a13-105">Con cinco métodos de conexión distintos en sesiones diversas de Windows PowerShell, el escritorio podría tener este aspecto:</span><span class="sxs-lookup"><span data-stu-id="77a13-105">With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![Cinco consolas de Windows PowerShell en ejecución al mismo tiempo](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="77a13-107">Esto no es ideal para la administración de Microsoft 365 porque no podemos intercambiar datos entre esas cinco ventanas para la administración entre servicios.</span><span class="sxs-lookup"><span data-stu-id="77a13-107">This is not optimal for managing Microsoft 365 because you can't exchange data among those five windows for cross-service management.</span></span> <span data-ttu-id="77a13-108">Este tema describe cómo usar una única instancia de Windows PowerShell desde la que administrar cuentas de Microsoft 365, SharePoint Online, Exchange Online, Skype Empresarial Online, Microsoft Teams y el Centro de cumplimiento &amp; seguridad.</span><span class="sxs-lookup"><span data-stu-id="77a13-108">This topic describes how to use a single instance of Windows PowerShell from which you can manage Microsoft 365 accounts, Skype for Business Online, Exchange Online, SharePoint Online, Microsoft Teams, and the Security &amp; Compliance Center.</span></span>

>[!Note]
><span data-ttu-id="77a13-109">Actualmente, este artículo solo contiene los comandos para conectarse a la nube mundial (+GCC).</span><span class="sxs-lookup"><span data-stu-id="77a13-109">This article currently only contains the commands to connect to the Worldwide (+GCC) cloud.</span></span> <span data-ttu-id="77a13-110">En las notas adicionales tiene vínculos a artículos que explican cómo conectarse a otras nubes de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="77a13-110">Additional notes provide links to articles with information about connecting to the other Microsoft 365 clouds.</span></span>
>

## <a name="before-you-begin"></a><span data-ttu-id="77a13-111">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="77a13-111">Before you begin</span></span>

<span data-ttu-id="77a13-112">Antes de poder administrar todo Microsoft 365 desde una sola instancia de Windows PowerShell, tenga en cuenta los siguientes requisitos previos:</span><span class="sxs-lookup"><span data-stu-id="77a13-112">Before you can manage all of Microsoft 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="77a13-113">La cuenta profesional o educativa de Microsoft 365 que use para estos procedimientos tiene que ser un miembro del rol de administrador de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="77a13-113">The Microsoft 365 work or school account that you use for these procedures needs to be a member of a Microsoft 365 admin role.</span></span> <span data-ttu-id="77a13-114">Para obtener más información, vea [Asignar roles de administrador](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide).</span><span class="sxs-lookup"><span data-stu-id="77a13-114">For more information, see [About admin roles](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide).</span></span> <span data-ttu-id="77a13-115">Este es un requisito de PowerShell para Microsoft 365, no necesariamente para todos los demás servicios de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="77a13-115">This a requirement for PowerShell for Microsoft 365, not necessarily for all other Microsoft 365 services.</span></span>
    
- <span data-ttu-id="77a13-116">Puede usar las siguientes versiones de Windows de 64 bits:</span><span class="sxs-lookup"><span data-stu-id="77a13-116">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="77a13-117">Windows 10</span><span class="sxs-lookup"><span data-stu-id="77a13-117">Windows 10</span></span>
    
  - <span data-ttu-id="77a13-118">Windows 8.1 o Windows 8</span><span class="sxs-lookup"><span data-stu-id="77a13-118">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="77a13-119">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="77a13-119">Windows Server 2019</span></span>
    
  - <span data-ttu-id="77a13-120">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="77a13-120">Windows Server 2016</span></span>
    
  - <span data-ttu-id="77a13-121">Windows Server 2012 R2 o Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="77a13-121">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="77a13-122">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="77a13-122">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="77a13-123">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="77a13-123">Windows Server 2008 R2 SP1\*</span></span>
    
    <span data-ttu-id="77a13-124">\* Es necesario instalar Microsoft .NET Framework 4.5.*x* y, luego, Windows Management Framework 3.0 o Windows Management Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="77a13-124">\* You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0.</span></span> <span data-ttu-id="77a13-125">Para más información, consulte [Instalación de .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) y [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) o [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span><span class="sxs-lookup"><span data-stu-id="77a13-125">For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="77a13-126">Debe usar una versión de 64 bits de Windows para cumplir los requisitos del módulo Skype Empresarial Online y uno de los módulos de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="77a13-126">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Microsoft 365 modules.</span></span>
    
- <span data-ttu-id="77a13-127">Debe instalar los módulos necesarios para Azure Active Directory (Azure AD), Exchange Online, SharePoint Online, Skype Empresarial Online y Teams:</span><span class="sxs-lookup"><span data-stu-id="77a13-127">You need to install the modules that are required for Azure Active Directory (Azure AD), Exchange Online, SharePoint Online, Skype for Business Online and Teams:</span></span>
    
   - [<span data-ttu-id="77a13-128">Azure Active Directory V2</span><span class="sxs-lookup"><span data-stu-id="77a13-128">Azure Active Directory V2</span></span>](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [<span data-ttu-id="77a13-129">Shell de administración de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="77a13-129">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="77a13-130">Skype Empresarial Online, módulo de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="77a13-130">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
   - [<span data-ttu-id="77a13-131">Exchange Online PowerShell V2</span><span class="sxs-lookup"><span data-stu-id="77a13-131">Exchange Online PowerShell V2</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell-v2/exchange-online-powershell-v2?view=exchange-ps#install-and-maintain-the-exchange-online-powershell-v2-module)
   - [<span data-ttu-id="77a13-132">Descripción de PowerShell para Teams</span><span class="sxs-lookup"><span data-stu-id="77a13-132">Teams PowerShell Overview</span></span>](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
    
-  <span data-ttu-id="77a13-133">Windows PowerShell necesita configurarse para ejecutar scripts firmados en Skype Empresarial Online y en el Centro de seguridad &amp; cumplimiento.</span><span class="sxs-lookup"><span data-stu-id="77a13-133">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="77a13-134">Para ello, ejecute el siguiente comando en una sesión de Windows PowerShell con permisos elevados (es decir, una ventana de Windows PowerShell que se abre seleccionando **Ejecutar como administrador**):</span><span class="sxs-lookup"><span data-stu-id="77a13-134">To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
   ```powershell
   Set-ExecutionPolicy RemoteSigned
   ```

## <a name="connection-steps-when-using-just-a-password"></a><span data-ttu-id="77a13-135">Pasos de conexión al usar solo una contraseña</span><span class="sxs-lookup"><span data-stu-id="77a13-135">Connection steps when using just a password</span></span>

<span data-ttu-id="77a13-136">Estos son los pasos para conectarse a todos los servicios en una única ventana de PowerShell cuando se usa solo una contraseña para iniciar sesión.</span><span class="sxs-lookup"><span data-stu-id="77a13-136">Here are the steps to connect to all the services in a single PowerShell window when you are using just a password for sign-in.</span></span>
  
1. <span data-ttu-id="77a13-137">Abra Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="77a13-137">Open Windows PowerShell.</span></span>
    
2. <span data-ttu-id="77a13-138">Ejecute este comando y escriba las credenciales de su cuenta profesional o educativa de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="77a13-138">Run this command and enter your Microsoft 365 work or school account credentials.</span></span>
    
   ```powershell
   $credential = Get-Credential
   ```

3. <span data-ttu-id="77a13-139">Ejecute este comando para conectarse a Azure AD con el módulo Azure Active Directory PowerShell para Graph.</span><span class="sxs-lookup"><span data-stu-id="77a13-139">Run this command to connect to Azure AD using the Azure Active Directory PowerShell for Graph module.</span></span>
    
   ```powershell
   Connect-AzureAD -Credential $credential
   ```
  
   <span data-ttu-id="77a13-140">Si usa el Módulo Microsoft Azure Active Directory para Windows PowerShell, también puede ejecutar este comando.</span><span class="sxs-lookup"><span data-stu-id="77a13-140">Alternately, if you are using the Microsoft Azure Active Directory Module for Windows PowerShell module, run this command.</span></span>
      
   ```powershell
   Connect-MsolService -Credential $credential
   ```

   > [!Note]
   > <span data-ttu-id="77a13-141">PowerShell Core no es compatible con el Módulo Microsoft Azure Active Directory para Windows PowerShell ni los cmdlet que llevan **Msol** en su nombre.</span><span class="sxs-lookup"><span data-stu-id="77a13-141">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="77a13-142">Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="77a13-142">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>

4. <span data-ttu-id="77a13-143">Ejecute estos comandos para conectarse a SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="77a13-143">Run these commands to connect to SharePoint Online.</span></span> <span data-ttu-id="77a13-144">Especifique el nombre de la organización para su dominio.</span><span class="sxs-lookup"><span data-stu-id="77a13-144">Specify the organization name for your domain.</span></span> <span data-ttu-id="77a13-145">Por ejemplo, para "litwareinc.onmicrosoft.com", el valor del nombre de la organización es "litwareinc".</span><span class="sxs-lookup"><span data-stu-id="77a13-145">For example, for "litwareinc.onmicrosoft.com", the  organization name value is "litwareinc".</span></span>
    
   ```powershell
   $orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
   Connect-SPOService -Url https://$orgName-admin.sharepoint.com -Credential $userCredential
   ```

5. <span data-ttu-id="77a13-146">Ejecute estos comandos para conectarse a Skype Empresarial Online.</span><span class="sxs-lookup"><span data-stu-id="77a13-146">Run these commands to connect to Skype for Business Online.</span></span> <span data-ttu-id="77a13-147">La primera vez que se conecte, verá una advertencia sobre el aumento del valor `WSMan NetworkDelayms` que debe omitir.</span><span class="sxs-lookup"><span data-stu-id="77a13-147">A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
     
   ```powershell
   Import-Module SkypeOnlineConnector
   $sfboSession = New-CsOnlineSession -Credential $credential
   Import-PSSession $sfboSession
   ```

6. <span data-ttu-id="77a13-148">Ejecute este comando para conectarse a Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="77a13-148">Run this command to connect to Exchange Online.</span></span>
    
   ```powershell
   Connect-ExchangeOnline -Credential $credential -ShowProgress $true
   ```

   > [!Note]
   > <span data-ttu-id="77a13-149">Para conectarse a Exchange Online para las nubes de Microsoft 365 que no sean mundiales, use el parámetro **-ExchangeEnvironmentName**.</span><span class="sxs-lookup"><span data-stu-id="77a13-149">To connect to Exchange Online for Microsoft 365 clouds other than Worldwide, use the **-ExchangeEnvironmentName** parameter.</span></span> <span data-ttu-id="77a13-150">Para obtener más información, consulte [Connect-ExchangeOnline](https://docs.microsoft.com/powershell/module/exchange/powershell-v2-module/connect-exchangeonline?view=exchange-ps).</span><span class="sxs-lookup"><span data-stu-id="77a13-150">See [Connect-ExchangeOnline](https://docs.microsoft.com/powershell/module/exchange/powershell-v2-module/connect-exchangeonline?view=exchange-ps) for more information.</span></span>

7. <span data-ttu-id="77a13-151">Ejecute estos comandos para conectarse a Teams PowerShell.</span><span class="sxs-lookup"><span data-stu-id="77a13-151">Run these commands to connect to Teams PowerShell.</span></span>
    
   ```powershell
   Import-Module MicrosoftTeams
   Connect-MicrosoftTeams -Credential $credential
   ```
  
   > [!Note]
   > <span data-ttu-id="77a13-152">Para conectarse a nubes de Microsoft Teams que no sean mundiales, consulte [Connect-MicrosoftTeams](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps).</span><span class="sxs-lookup"><span data-stu-id="77a13-152">To connect to Microsoft Teams clouds other than Worldwide, see [Connect-MicrosoftTeams](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps).</span></span>

8. <span data-ttu-id="77a13-153">Ejecute estos comandos para conectarse al Centro de seguridad &amp; cumplimiento.</span><span class="sxs-lookup"><span data-stu-id="77a13-153">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
   ```powershell
   $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
   Import-PSSession $SccSession -Prefix cc
   ```

   > [!Note]
   > <span data-ttu-id="77a13-154">Para conectarse al Centro de seguridad &amp; cumplimiento para nubes de Microsoft 365 que no sean mundiales, vea [Conectar con el Centro de seguridad y cumplimiento de PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span><span class="sxs-lookup"><span data-stu-id="77a13-154">To connect to the Security &amp; Compliance Center for Microsoft 365 clouds other than Worldwide, see [Connect to Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span></span>

<span data-ttu-id="77a13-155">Aquí tiene todos los comandos en un único bloque cuando se usa el módulo Azure Active Directory PowerShell para Graph.</span><span class="sxs-lookup"><span data-stu-id="77a13-155">Here are all the commands in a single block when using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="77a13-156">Especifique el nombre del host de su dominio y, a continuación, ejecútelos todos a la vez.</span><span class="sxs-lookup"><span data-stu-id="77a13-156">Specify the name of your domain host, and then run them all at one time.</span></span>
  
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

<span data-ttu-id="77a13-157">Como alternativa, estos son todos los comandos en un único bloque cuando se usa el Módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="77a13-157">Alternately, here are all the commands in a single block when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span> <span data-ttu-id="77a13-158">Especifique el nombre del host de su dominio y, a continuación, ejecútelos todos a la vez.</span><span class="sxs-lookup"><span data-stu-id="77a13-158">Specify the name of your domain host, and then run them all at one time.</span></span>
  
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

<span data-ttu-id="77a13-159">Cuando esté listo para cerrar la ventana de Windows PowerShell, ejecute este comando para quitar las sesiones activas de Skype Empresarial Online, SharePoint Online, el Centro de seguridad &amp; cumplimiento y Teams:</span><span class="sxs-lookup"><span data-stu-id="77a13-159">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, SharePoint Online, the Security &amp; Compliance Center, and Teams:</span></span>
  
```powershell
Remove-PSSession $sfboSession ; Remove-PSSession $SccSession ; Disconnect-SPOService ; Disconnect-MicrosoftTeams 
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a><span data-ttu-id="77a13-160">Pasos de conexión al usar autenticación multifactor</span><span class="sxs-lookup"><span data-stu-id="77a13-160">Connection steps when using multi-factor authentication</span></span>

<span data-ttu-id="77a13-161">Estos son todos los comandos de un único bloque para conectarse a Azure AD, SharePoint Online, Skype Empresarial, Exchange Online y Teams mediante la autenticación multifactor en una única ventana con el módulo Azure Active Directory PowerShell para Graph.</span><span class="sxs-lookup"><span data-stu-id="77a13-161">Here are all the commands in a single block to connect to Azure AD, SharePoint Online, Skype for Business, Exchange Online, and Teams using multi-factor authentication in a single window using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="77a13-162">Especifique el nombre de usuario principal (UPN) de una cuenta de usuario y el nombre de host del dominio y, a continuación, ejecútelos todos al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="77a13-162">Specify the user principal name (UPN) name of a user account and your domain host name, and then run them all at one time.</span></span>

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

<span data-ttu-id="77a13-163">Como alternativa, estos son todos los comandos cuando use el Módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="77a13-163">Alternately, here are all the commands when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span>

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

<span data-ttu-id="77a13-164">Para obtener más datos sobre el Centro de seguridad &amp; cumplimiento, vea [Conectarse al Centro de seguridad y cumplimiento de PowerShell con la autenticación multifactor](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps) para conectarse mediante la autenticación multifactor:</span><span class="sxs-lookup"><span data-stu-id="77a13-164">For the Security &amp; Compliance Center, see [Connect to Security & Compliance Center PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps) to connect using multi-factor authentication:</span></span>

## <a name="see-also"></a><span data-ttu-id="77a13-165">Recursos adicionales</span><span class="sxs-lookup"><span data-stu-id="77a13-165">See also</span></span>

- [<span data-ttu-id="77a13-166">Conectarse a Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="77a13-166">Connect to Microsoft 365 with PowerShell</span></span>](connect-to-office-365-powershell.md)
- [<span data-ttu-id="77a13-167">Administrar SharePoint Online con PowerShell</span><span class="sxs-lookup"><span data-stu-id="77a13-167">Manage SharePoint Online with PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="77a13-168">Administrar cuentas de usuario, licencias y grupos de Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="77a13-168">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="77a13-169">Usar Windows PowerShell para crear informes en Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="77a13-169">Use Windows PowerShell to create reports in Microsoft 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
