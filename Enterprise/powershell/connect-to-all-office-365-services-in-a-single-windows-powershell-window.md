---
title: Conectarse a todos los servicios de Office 365 en una sola ventana de Windows PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/23/2018
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
ms.openlocfilehash: 7e3a3ecbb0526c88392848cf39b59b40f1f4c80c
ms.sourcegitcommit: 3b474e0b9f0c12bb02f8439fb42b80c2f4798ce1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="2fe19-103">Conectarse a todos los servicios de Office 365 en una sola ventana de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2fe19-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

 <span data-ttu-id="2fe19-104">**Resumen:** En lugar de administrar diferentes servicios de Office 365 en distintas ventanas de la consola de PowerShell, puede conectarse a todos los servicios de Office 365 y gestionarlos desde la ventana de consola única.</span><span class="sxs-lookup"><span data-stu-id="2fe19-104">**Summary:** Instead of managing different Office 365 services in separate PowerShell console windows, you can connect to all Office 365 services and manage them from single console window.</span></span>
  
<span data-ttu-id="2fe19-p101">Al usar PowerShell para administrar Office 365, es posible tener hasta cinco sesiones diferentes de Windows PowerShell abierto al mismo tiempo correspondiente al centro de administración de Office 365, SharePoint Online, Exchange Online, Skype para los negocios en línea y la seguridad &amp;Centro de cumplimiento. Con cinco métodos de conexión diferentes en las sesiones de Windows PowerShell independientes, el escritorio tendría la apariencia siguiente:</span><span class="sxs-lookup"><span data-stu-id="2fe19-p101">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Office 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, and the Security &amp; Compliance Center. With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![Cinco consolas de Windows PowerShell en ejecución al mismo tiempo](images/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="2fe19-p102">Esto no es óptimo para la administración de Office 365 porque no pueden intercambiar datos entre esos cinco ventanas de administración de servicio de la cruz. Este tema describe cómo utilizar una única instancia de Windows PowerShell desde el que puede administrar la seguridad, Skype para los negocios en línea, Exchange Online, SharePoint Online y Office 365 &amp; centro de cumplimiento.</span><span class="sxs-lookup"><span data-stu-id="2fe19-p102">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management. This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="2fe19-110">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="2fe19-110">Before you begin</span></span>
<span data-ttu-id="2fe19-111"><a name="BeforeYouBegin"> </a></span><span class="sxs-lookup"><span data-stu-id="2fe19-111"></span></span>

<span data-ttu-id="2fe19-112">Para poder administrar todo Office 365 desde una sola instancia de Windows PowerShell, tenga en cuenta los siguientes requisitos previos:</span><span class="sxs-lookup"><span data-stu-id="2fe19-112">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="2fe19-p103">El Office 365 trabajo o escuela cuenta utilizar para estos procedimientos necesidades para ser miembro de una función de administración de Office 365. Para obtener más información, consulte [las funciones de administrador acerca de Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367). Este requisito para Office 365 PowerShell, pero no necesariamente para todos los demás servicios de Office 365.</span><span class="sxs-lookup"><span data-stu-id="2fe19-p103">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367). This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="2fe19-116">Puede usar las siguientes versiones de Windows de 64 bits:</span><span class="sxs-lookup"><span data-stu-id="2fe19-116">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="2fe19-117">Windows 10</span><span class="sxs-lookup"><span data-stu-id="2fe19-117">Windows 10</span></span>
    
  - <span data-ttu-id="2fe19-118">Windows 8.1 o Windows 8</span><span class="sxs-lookup"><span data-stu-id="2fe19-118">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="2fe19-119">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="2fe19-119">Windows Server 2016</span></span>
    
  - <span data-ttu-id="2fe19-120">Windows Server 2012 R2 o Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="2fe19-120">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="2fe19-121">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="2fe19-121">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="2fe19-122">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="2fe19-122">Windows Server 2008 R2 SP1\*</span></span>
    
    * <span data-ttu-id="2fe19-p104">Debe instalar el Microsoft.NET Framework 4.5. *x* y, a continuación, el Windows Management Framework 3.0 o el marco de trabajo de administración de Windows 4.0. Para obtener más información, vea [instalar el.NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) y [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) o [4.0 de Windows Management Framework](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span><span class="sxs-lookup"><span data-stu-id="2fe19-p104">You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0. For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="2fe19-125">Debe utilizar una versión de 64 bits de Windows debido a los requisitos para el Skype para el módulo de negocios en línea y uno de los módulos de Office 365.</span><span class="sxs-lookup"><span data-stu-id="2fe19-125">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="2fe19-126">Debe instalar los módulos que son necesarios para AD Azure, SharePoint Online y Skype para los negocios en línea:</span><span class="sxs-lookup"><span data-stu-id="2fe19-126">You need to install the modules that are required for Azure AD, SharePoint Online, and Skype for Business Online:</span></span>
    
   - [<span data-ttu-id="2fe19-127">Azure de Active Directory V2</span><span class="sxs-lookup"><span data-stu-id="2fe19-127">Azure Active Directory V2</span></span>](connect-to-office-365-powershell.md#ConnectV2)
   - [<span data-ttu-id="2fe19-128">Shell de administración en línea de SharePoint</span><span class="sxs-lookup"><span data-stu-id="2fe19-128">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="2fe19-129">Skype para el negocio en línea, módulo de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2fe19-129">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  <span data-ttu-id="2fe19-p105">Windows PowerShell debe configurarse para ejecutar secuencias de comandos firmadas de Skype para los negocios en línea, Exchange Online y la seguridad &amp; centro de cumplimiento. Para ello, ejecute el siguiente comando en una sesión de Windows PowerShell con privilegios elevados (una ventana de Windows PowerShell que abra seleccionando **Ejecutar como administrador**).</span><span class="sxs-lookup"><span data-stu-id="2fe19-p105">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center. To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a><span data-ttu-id="2fe19-132">Pasos de conexión cuando se utiliza una contraseña</span><span class="sxs-lookup"><span data-stu-id="2fe19-132">Connection steps when using a password</span></span>
<span data-ttu-id="2fe19-133"><a name="ConnStepsPassword"> </a></span><span class="sxs-lookup"><span data-stu-id="2fe19-133"></span></span>

<span data-ttu-id="2fe19-134">Estos son los pasos para conectarse a todos los servicios en una sola ventana de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2fe19-134">Here are the steps to connect to all the services in a single PowerShell window.</span></span>
  
1. <span data-ttu-id="2fe19-135">Abrir Windows PowerShell como administrador (uso de **Ejecutar como administrador**).</span><span class="sxs-lookup"><span data-stu-id="2fe19-135">Open Windows PowerShell as an administrator (use **Run as administrator**).</span></span>
    
2. <span data-ttu-id="2fe19-136">Ejecute este comando y especifique su trabajo en Office 365 o credenciales de la cuenta de la escuela.</span><span class="sxs-lookup"><span data-stu-id="2fe19-136">Run this command, and enter your Office 365 work or school account credentials.</span></span>
    
  ```
  $credential = Get-Credential
  ```

3. <span data-ttu-id="2fe19-137">Ejecute este comando para conectar a Azure Active Directory (AD).</span><span class="sxs-lookup"><span data-stu-id="2fe19-137">Run this command to connect to Azure Active Directory (AD).</span></span>
    
  ```
   Connect-AzureAD -Credential $credential
  ```

4. <span data-ttu-id="2fe19-p106">Ejecutar estos comandos para conectarse a SharePoint Online. Reemplazar _ \<domainhost >_ con el valor real de su dominio. Por ejemplo, para `litwareinc.onmicrosoft.com`, el _ \<domainhost >_ valor es `litwareinc`.</span><span class="sxs-lookup"><span data-stu-id="2fe19-p106">Run these commands to connect to SharePoint Online. Replace  _\<domainhost>_ with the actual value for your domain. For example, for `litwareinc.onmicrosoft.com`, the  _\<domainhost>_ value is `litwareinc`.</span></span>
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="2fe19-p107">Ejecutar estos comandos para conectar con Skype para los negocios en línea. Una advertencia acerca de cómo aumentar el `WSMan NetworkDelayms` valor se espera la primera vez que se conecta y se debe omitir.</span><span class="sxs-lookup"><span data-stu-id="2fe19-p107">Run these commands to connect to Skype for Business Online. A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="2fe19-143">Ejecutar estos comandos para conectarse a Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="2fe19-143">Run these commands to connect to Exchange Online.</span></span>
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession
  ```

7. <span data-ttu-id="2fe19-144">Ejecutar estos comandos para conectarse a la seguridad &amp; centro de cumplimiento.</span><span class="sxs-lookup"><span data-stu-id="2fe19-144">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

<span data-ttu-id="2fe19-p108">Aquí están todos los comandos en un único bloque. Especificar el nombre del host de dominio y, a continuación, ejecutarlos todos al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="2fe19-p108">Here are all the commands in a single block. Specify the name of your domain host, and then run them all at one time.</span></span>
  
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
<span data-ttu-id="2fe19-147">Cuando esté listo para cerrar la ventana de Windows PowerShell, ejecute este comando para eliminar las sesiones activas en Skype para los negocios en línea, Exchange Online, SharePoint Online y la seguridad &amp; centro de cumplimiento de normas:</span><span class="sxs-lookup"><span data-stu-id="2fe19-147">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:</span></span>
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $SccSession ; Disconnect-SPOService
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a><span data-ttu-id="2fe19-148">Pasos de conexión cuando se utiliza la autenticación con varios factores</span><span class="sxs-lookup"><span data-stu-id="2fe19-148">Connection steps when using multi-factor authentication</span></span>
<span data-ttu-id="2fe19-149"><a name="ConnStepsMFA"> </a></span><span class="sxs-lookup"><span data-stu-id="2fe19-149"></span></span>

<span data-ttu-id="2fe19-p109">Aquí están todos los comandos en un único bloque para conectarse a AD Azure, SharePoint Online y Skype para negocios mediante autenticación con varios factores en una sola ventana. Especificar el nombre de usuario nombre principal (UPN) de una cuenta de administrador global y el nombre de host del dominio y, a continuación, ejecutarlos todos al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="2fe19-p109">Here are all the commands in a single block to connect to Azure AD, SharePoint Online, and Skype for Buiness using multi-factor authentication in a single window. Specify the user principal name (UPN) name of a global administrator account and your domain host name, and then run them all at one time.</span></span>

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

<span data-ttu-id="2fe19-152">Para Exchange Online y la seguridad &amp; centro de cumplimiento de normas, vea los temas siguientes para conectarse mediante la autenticación de varios factor:</span><span class="sxs-lookup"><span data-stu-id="2fe19-152">For Exchange Online and the Security &amp; Compliance Center, see the following topics to connect using multi-factor authentication:</span></span>

- [<span data-ttu-id="2fe19-153">Conectar con PowerShell en línea de Exchange mediante la autenticación con varios factores</span><span class="sxs-lookup"><span data-stu-id="2fe19-153">Connect to Exchange Online PowerShell using multi-factor authentication</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell)
- [<span data-ttu-id="2fe19-154">Conectarse a Office 365 seguridad & PowerShell de centro de cumplimiento de normas mediante la autenticación con varios factores</span><span class="sxs-lookup"><span data-stu-id="2fe19-154">Connect to Office 365 Security & Compliance Center PowerShell using multi-factor authentication</span></span>](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)
 
<span data-ttu-id="2fe19-155">Tenga en cuenta que en ambos casos, debe conectar con sesiones separadas del Exchange Online remoto PowerShell módulo.</span><span class="sxs-lookup"><span data-stu-id="2fe19-155">Note that in both cases, you must connect using separate sessions of the Exchange Online Remote PowerShell Module.</span></span>


## <a name="new-to-office-365"></a><span data-ttu-id="2fe19-156">¿Es la primera vez que usa Office 365?</span><span class="sxs-lookup"><span data-stu-id="2fe19-156">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="2fe19-157">Consulte también</span><span class="sxs-lookup"><span data-stu-id="2fe19-157">See also</span></span>

- [<span data-ttu-id="2fe19-158">Conectarse a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="2fe19-158">Connect to Office 365 PowerShell</span></span>](connect-to-office-365-powershell.md)
- [<span data-ttu-id="2fe19-159">Administrar SharePoint Online con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="2fe19-159">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="2fe19-160">Administrar licencias y cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="2fe19-160">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="2fe19-161">Usar Windows PowerShell para crear informes en Office 365</span><span class="sxs-lookup"><span data-stu-id="2fe19-161">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
