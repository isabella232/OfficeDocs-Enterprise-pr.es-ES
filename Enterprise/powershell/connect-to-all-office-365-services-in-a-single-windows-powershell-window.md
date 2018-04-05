---
title: Conectarse a todos los servicios de Office 365 en una sola ventana de Windows PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/04/2018
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
description: 'Resumen: Conectar Windows PowerShell con todos los servicios de Office 365 en una sola ventana de Windows PowerShell.'
ms.openlocfilehash: ccd8ed1dc53d306aa77d79ac0270f5bd24dd9298
ms.sourcegitcommit: 21cc62118b78b76d16ef12e2c3eff2c0c789e3d0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2018
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="42d22-103">Conectarse a todos los servicios de Office 365 en una sola ventana de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="42d22-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

 <span data-ttu-id="42d22-104">**Resumen:** En lugar de administrar diferentes servicios de Office 365 en distintas ventanas de la consola de PowerShell, puede conectarse a todos los servicios de Office 365 y gestionarlos desde la ventana de consola única.</span><span class="sxs-lookup"><span data-stu-id="42d22-104">**Summary:** Instead of managing different Office 365 services in separate PowerShell console windows, you can connect to all Office 365 services and manage them from single console window.</span></span>
  
<span data-ttu-id="42d22-p101">Al usar PowerShell para administrar Office 365, es posible tener hasta cinco sesiones diferentes de Windows PowerShell abierto al mismo tiempo correspondiente al centro de administración de Office 365, SharePoint Online, Exchange Online, Skype para los negocios en línea y la seguridad &amp;Centro de cumplimiento. Con cinco métodos de conexión diferentes en las sesiones de Windows PowerShell independientes, el escritorio tendría la apariencia siguiente:</span><span class="sxs-lookup"><span data-stu-id="42d22-p101">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Office 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, and the Security &amp; Compliance Center. With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![Cinco consolas de Windows PowerShell en ejecución al mismo tiempo](images/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="42d22-p102">Esto no es óptimo para la administración de Office 365 porque no pueden intercambiar datos entre esos cinco ventanas de administración de servicio de la cruz. Este tema describe cómo utilizar una única instancia de Windows PowerShell desde el que puede administrar la seguridad, Skype para los negocios en línea, Exchange Online, SharePoint Online y Office 365 &amp; centro de cumplimiento.</span><span class="sxs-lookup"><span data-stu-id="42d22-p102">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management. This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center.</span></span>

>[!Note]
><span data-ttu-id="42d22-110">Este artículo es que se está actualizando para utilizar el módulo de Active Directory V2 PowerShell de Azure y para la autenticación con varios factores (AMF).</span><span class="sxs-lookup"><span data-stu-id="42d22-110">This article is in the process of being updated to use the Azure Active Directory V2 PowerShell module and for multifactor authentication (MFA).</span></span>
>
  
## <a name="before-you-begin"></a><span data-ttu-id="42d22-111">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="42d22-111">Before you begin</span></span>
<span data-ttu-id="42d22-112"><a name="BeforeYouBegin"> </a></span><span class="sxs-lookup"><span data-stu-id="42d22-112"></span></span>

<span data-ttu-id="42d22-113">Para poder administrar todo Office 365 desde una sola instancia de Windows PowerShell, tenga en cuenta los siguientes requisitos previos:</span><span class="sxs-lookup"><span data-stu-id="42d22-113">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="42d22-p103">El Office 365 trabajo o escuela cuenta utilizar para estos procedimientos necesidades para ser miembro de una función de administración de Office 365. Para obtener más información, consulte [las funciones de administrador acerca de Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367). Este requisito para Office 365 PowerShell, pero no necesariamente para todos los demás servicios de Office 365.</span><span class="sxs-lookup"><span data-stu-id="42d22-p103">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367). This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="42d22-117">Puede usar las siguientes versiones de Windows de 64 bits:</span><span class="sxs-lookup"><span data-stu-id="42d22-117">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="42d22-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="42d22-118">Windows 10</span></span>
    
  - <span data-ttu-id="42d22-119">Windows 8.1 o Windows 8</span><span class="sxs-lookup"><span data-stu-id="42d22-119">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="42d22-120">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="42d22-120">Windows Server 2016</span></span>
    
  - <span data-ttu-id="42d22-121">Windows Server 2012 R2 o Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="42d22-121">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="42d22-122">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="42d22-122">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="42d22-123">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="42d22-123">Windows Server 2008 R2 SP1\*</span></span>
    
    * <span data-ttu-id="42d22-p104">Debe instalar el Microsoft.NET Framework 4.5. *x* y, a continuación, el Windows Management Framework 3.0 o el marco de trabajo de administración de Windows 4.0. Para obtener más información, vea [instalar el.NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) y [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) o [4.0 de Windows Management Framework](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span><span class="sxs-lookup"><span data-stu-id="42d22-p104">You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0. For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="42d22-126">Debe utilizar una versión de 64 bits de Windows debido a los requisitos para el Skype para el módulo de negocios en línea y uno de los módulos de Office 365.</span><span class="sxs-lookup"><span data-stu-id="42d22-126">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="42d22-127">Debe instalar los módulos necesarios para Office 365, SharePoint Online y Skype para los negocios en línea:</span><span class="sxs-lookup"><span data-stu-id="42d22-127">You need to install the modules that are required for Office 365, SharePoint Online, and Skype for Business Online:</span></span>
    
   - [<span data-ttu-id="42d22-128">Servicio en línea Sign-in Ayudante de Microsoft para profesionales de TI RTW</span><span class="sxs-lookup"><span data-stu-id="42d22-128">Microsoft Online Service Sign-in Assistant for IT Professionals RTW</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=286152)
   - <span data-ttu-id="42d22-129">Windows Azure Active Directory módulo para Windows PowerShell (versión de 64 bits) con el comando **Install-módulo MSOnline** en una línea de comandos de PowerShell elevado.</span><span class="sxs-lookup"><span data-stu-id="42d22-129">Windows Azure Active Directory Module for Windows PowerShell (64-bit version) with the **Install-Module MSOnline** command at an elevated PowerShell command prompt.</span></span>
   - [<span data-ttu-id="42d22-130">Shell de administración en línea de SharePoint</span><span class="sxs-lookup"><span data-stu-id="42d22-130">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="42d22-131">Skype para el negocio en línea, módulo de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="42d22-131">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  <span data-ttu-id="42d22-p105">Windows PowerShell debe configurarse para ejecutar secuencias de comandos firmadas de Skype para los negocios en línea, Exchange Online y la seguridad &amp; centro de cumplimiento. Para ello, ejecute el siguiente comando en una sesión de Windows PowerShell con privilegios elevados (una ventana de Windows PowerShell que abra seleccionando **Ejecutar como administrador**).</span><span class="sxs-lookup"><span data-stu-id="42d22-p105">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center. To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps"></a><span data-ttu-id="42d22-134">Pasos de conexión</span><span class="sxs-lookup"><span data-stu-id="42d22-134">Connection steps</span></span>
<span data-ttu-id="42d22-135"><a name="BeforeYouBegin"> </a></span><span class="sxs-lookup"><span data-stu-id="42d22-135"></span></span>

<span data-ttu-id="42d22-136">Estos son los pasos para conectarse a todos los servicios en una sola ventana de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="42d22-136">Here are the steps to connect to all the services in a single PowerShell window.</span></span>
  
1. <span data-ttu-id="42d22-137">Abrir Windows PowerShell como administrador (uso de **Ejecutar como administrador**).</span><span class="sxs-lookup"><span data-stu-id="42d22-137">Open Windows PowerShell as an administrator (use **Run as administrator**).</span></span>
    
2. <span data-ttu-id="42d22-138">Ejecute este comando y especifique su trabajo en Office 365 o credenciales de la cuenta de la escuela.</span><span class="sxs-lookup"><span data-stu-id="42d22-138">Run this command, and enter your Office 365 work or school account credentials.</span></span>
    
  ```
  $credential = Get-Credential
  ```

3. <span data-ttu-id="42d22-139">Ejecutar estos comandos para conectarse a Office 365.</span><span class="sxs-lookup"><span data-stu-id="42d22-139">Run these commands to connect to Office 365.</span></span>
    
  ```
  Import-Module MsOnline
  Connect-MsolService -Credential $credential
  ```

4. <span data-ttu-id="42d22-p106">Ejecutar estos comandos para conectarse a SharePoint Online. Reemplazar _ \<domainhost >_ con el valor real de su dominio. Por ejemplo, para `litwareinc.onmicrosoft.com`, el _ \<domainhost >_ valor es `litwareinc`.</span><span class="sxs-lookup"><span data-stu-id="42d22-p106">Run these commands to connect to SharePoint Online. Replace  _\<domainhost>_ with the actual value for your domain. For example, for `litwareinc.onmicrosoft.com`, the  _\<domainhost>_ value is `litwareinc`.</span></span>
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="42d22-p107">Ejecutar estos comandos para conectar con Skype para los negocios en línea. Una advertencia acerca de cómo aumentar el `WSMan NetworkDelayms` valor se espera la primera vez que se conecta y se debe omitir.</span><span class="sxs-lookup"><span data-stu-id="42d22-p107">Run these commands to connect to Skype for Business Online. A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="42d22-145">Ejecutar estos comandos para conectarse a Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="42d22-145">Run these commands to connect to Exchange Online.</span></span>
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

7. <span data-ttu-id="42d22-146">Ejecutar estos comandos para conectarse a la seguridad &amp; centro de cumplimiento.</span><span class="sxs-lookup"><span data-stu-id="42d22-146">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```
  $ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
  Import-PSSession $ccSession -Prefix cc
  ```
> [!NOTE]
> <span data-ttu-id="42d22-p108">El prefijo de texto "cc" se agrega a *todos los* seguridad &amp; centro de cumplimiento de los nombres de cmdlet para poder ejecutar los cmdlets que existe en Exchange Online y la seguridad &amp; centro de cumplimiento en la misma sesión de Windows PowerShell. Por ejemplo, **Get-RoleGroup** pasa a ser **Get-ccRoleGroup** en la seguridad &amp; centro de cumplimiento.</span><span class="sxs-lookup"><span data-stu-id="42d22-p108">The text prefix "cc" is added to  *all*  Security &amp; Compliance Center cmdlet names so you can run cmdlets that exist in both Exchange Online and the Security &amp; Compliance Center in the same Windows PowerShell session. For example, **Get-RoleGroup** becomes **Get-ccRoleGroup** in the Security &amp; Compliance Center.</span></span>
  
<span data-ttu-id="42d22-p109">Aquí están todos los comandos en un único bloque. Especificar el nombre del host de dominio y, a continuación, ejecutarlos todos al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="42d22-p109">Here are all the commands in a single block. Specify the name of your domain host, and then run them all at one time.</span></span>
  
```
$domainHost="<domain host name, such as litware for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Import-Module MsOnline
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
Import-PSSession $ccSession -Prefix cc
```
<span data-ttu-id="42d22-151">Cuando esté listo para cerrar la ventana de Windows PowerShell, ejecute este comando para eliminar las sesiones activas en Skype para los negocios en línea, Exchange Online, SharePoint Online y la seguridad &amp; centro de cumplimiento de normas:</span><span class="sxs-lookup"><span data-stu-id="42d22-151">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:</span></span>
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $ccSession ; Disconnect-SPOService
```

## <a name="new-to-office-365"></a><span data-ttu-id="42d22-152">¿Es la primera vez que usa Office 365?</span><span class="sxs-lookup"><span data-stu-id="42d22-152">New to Office 365?</span></span>
<span data-ttu-id="42d22-153"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="42d22-153"></span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="42d22-154">Consulte también</span><span class="sxs-lookup"><span data-stu-id="42d22-154">See also</span></span>

- [<span data-ttu-id="42d22-155">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="42d22-155">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="42d22-156">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="42d22-156">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="42d22-157">Administrar SharePoint Online con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="42d22-157">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="42d22-158">Administrar licencias y cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="42d22-158">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="42d22-159">Usar Windows PowerShell para crear informes en Office 365</span><span class="sxs-lookup"><span data-stu-id="42d22-159">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
