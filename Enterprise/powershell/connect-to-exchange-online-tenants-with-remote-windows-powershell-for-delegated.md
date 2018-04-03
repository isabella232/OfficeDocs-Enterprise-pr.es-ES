---
title: Conectarse a los inquilinos de Exchange Online con el modo remoto de Windows PowerShell para asociados con permiso de acceso delegado (DAP)
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: ae5f1a87-8b77-4f93-a1b8-56f800aeb283
description: 'Resumen: Use el modo remoto de Windows PowerShell para conectarse a Exchange Online con el parámetro DelegatedOrg.'
ms.openlocfilehash: d8cbb6640419ba2f1de868ae88b0a273c3f71ae7
ms.sourcegitcommit: f3f81d2c2e8290948d93f3f787a679c804840256
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/23/2018
---
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="89e82-103">Conectarse a los inquilinos de Exchange Online con el modo remoto de Windows PowerShell para asociados con permiso de acceso delegado (DAP)</span><span class="sxs-lookup"><span data-stu-id="89e82-103">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="89e82-104">**Resumen:** use el modo remoto de Windows PowerShell para conectarse a Exchange Online con el parámetro _DelegatedOrg_.</span><span class="sxs-lookup"><span data-stu-id="89e82-104">**Summary:** Use remote Windows PowerShell to connect to Exchange Online by using the _DelegatedOrg_ parameter.</span></span>
  
<span data-ttu-id="89e82-p101">El modo remoto de Windows PowerShell permite administrar la configuración de Exchange Online desde la línea de comandos. Use Windows PowerShell en el equipo local para crear una sesión remota a Exchange Online. Es un proceso de tres pasos en el que se especifican las credenciales de Exchange Online, se proporciona la configuración de conexión requerida y se importan los cmdlets de Exchange Online a la sesión local de Windows PowerShell para poder usarlos.</span><span class="sxs-lookup"><span data-stu-id="89e82-p101">Remote Windows PowerShell lets you manage your Exchange Online settings from the command line. You use Windows PowerShell on your local computer to create a remote session to Exchange Online. It's a three-step process where you enter your Exchange Online credentials, provide the required connection settings, and then import the Exchange Online cmdlets into your local Windows PowerShell session so that you can use them.</span></span>
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="89e82-108">¿Qué necesita saber antes de comenzar?</span><span class="sxs-lookup"><span data-stu-id="89e82-108">What do you need to know before you begin?</span></span>

- <span data-ttu-id="89e82-109">Tiempo estimado para finalizar: 5 minutos</span><span class="sxs-lookup"><span data-stu-id="89e82-109">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="89e82-110">Puede usar las siguientes versiones de Windows:</span><span class="sxs-lookup"><span data-stu-id="89e82-110">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="89e82-111">Windows 10</span><span class="sxs-lookup"><span data-stu-id="89e82-111">Windows 10</span></span>
    
  - <span data-ttu-id="89e82-112">Windows 8.1 o Windows 8</span><span class="sxs-lookup"><span data-stu-id="89e82-112">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="89e82-113">Windows Server 2012 R2 o Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="89e82-113">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="89e82-114">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="89e82-114">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="89e82-115">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="89e82-115">Windows Server 2008 R2 SP1\*</span></span>
    
    <span data-ttu-id="89e82-p102">\* Es necesario instalar .NET Framework 4.5.1 o .NET Framework 4.5 y, después, Windows Management Framework 4.0 o Windows Management Framework 3.0. Para obtener más información, vea los recursos siguientes:</span><span class="sxs-lookup"><span data-stu-id="89e82-p102">\*You need to install the .NET Framework 4.5.1 or the .NET Framework 4.5 and then either the Windows Management Framework 4.0 or the Windows Management Framework 3.0 . For more information, see the following resources:</span></span>
    
    - [<span data-ttu-id="89e82-118">Instalar .NET Framework</span><span class="sxs-lookup"><span data-stu-id="89e82-118">Installing the .NET Framework</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=257868)
    
    - <span data-ttu-id="89e82-119">[Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) o [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)</span><span class="sxs-lookup"><span data-stu-id="89e82-119">[Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)</span></span>
    
- <span data-ttu-id="89e82-120">Para obtener información acerca de los métodos abreviados de teclado que se pueden aplicar a los procedimientos de este tema, consulte [Métodos abreviados de teclado en el Centro de administración de Exchange](https://go.microsoft.com/fwlink/p/?LinkId=534017).</span><span class="sxs-lookup"><span data-stu-id="89e82-120">For information about keyboard shortcuts that might apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](https://go.microsoft.com/fwlink/p/?LinkId=534017).</span></span>
    
## 

> [!IMPORTANT]
> <span data-ttu-id="89e82-p103">Este procedimiento es solo paraasociados con permiso de acceso delegado (DAP). Si no es socio DAP, no use este procedimiento.</span><span class="sxs-lookup"><span data-stu-id="89e82-p103">This procedure is only for Delegated Access Permission (DAP) partners. If you are not a DAP partner, do not use this procedure.</span></span> 
  
<span data-ttu-id="89e82-p104">Los asociados con DAP son asociados de proveedor de soluciones en la nube (CSP) y redifusión web. Generalmente son proveedores de red o de telecomunicaciones para otras compañías. Empaquetan suscripciones en sus ofertas de servicio a sus clientes. Poseen un arrendamiento de asociado al que se le conceden automáticamente permisos Administrar en nombre de (AOBO) para susarrendamientos de cliente de Office 365, de modo que pueden administrar todos sus arrendamientos de cliente e informar al respecto.</span><span class="sxs-lookup"><span data-stu-id="89e82-p104">DAP partners are Syndication and Cloud Solution Providers (CSP) partners. They are frequently network or telecom providers to other companies. They bundle subscriptions into their service offerings to their customers. They own a partner tenancy that is automatically granted Administer On Behalf Of (AOBO) permissions to their Office 365customer tenancies so they can administer and report on all of their customer tenancies.</span></span>
  
## <a name="connect-to-exchange-online"></a><span data-ttu-id="89e82-127">Conectarse a Exchange Online</span><span class="sxs-lookup"><span data-stu-id="89e82-127">Connect to Exchange Online</span></span>

1. <span data-ttu-id="89e82-128">En el equipo local, abra Windows PowerShell y ejecute el siguiente comando.</span><span class="sxs-lookup"><span data-stu-id="89e82-128">On your local computer, open Windows PowerShell and run the following command.</span></span>
    
  ```
  $UserCredential = Get-Credential
  ```

    <span data-ttu-id="89e82-129">En el cuadro de diálogo **Solicitud de credenciales para Windows PowerShell**, escriba su nombre de usuario de administrador DAP y contraseña y, a continuación, haga clic en **Acepta**.</span><span class="sxs-lookup"><span data-stu-id="89e82-129">In the **Windows PowerShell Credential Request** dialog box, enter your DAP administrator user name and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="89e82-130">Ejecute el siguiente comando, reemplace el  _<customer tenant domain name>_ por el nombre de dominio del inquilino al que desee conectarse.</span><span class="sxs-lookup"><span data-stu-id="89e82-130">Run the following command, replacing  _<customer tenant domain name>_ with the name of the tenant domain that you want to connect to.</span></span>
    
  ```
  $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name>-Credential $UserCredential -Authentication Basic -AllowRedirection
  ```

    <span data-ttu-id="89e82-p105">El paso clave en este comando es especificar a qué cliente hay que acceder para obtener la información de supervisión. Esto se realiza en el parámetro  _ConnectionURI_, donde se proporciona el FQDN del nombre de dominio inicial como el valor para el parámetro _DelegatedOrg_. Esto indica al modo remoto de Windows PowerShell para Exchange Online para Windows PowerShell debe conectarse a los informes de Office 365 en el contexto de un cliente específico cada vez que un informe se ejecuta. Después de especificar el cliente, todos los comandos siguientes se ejecutan en el contexto de dicho cliente. Esto permite a los asociados acceder a todos los informes disponibles para este cliente.</span><span class="sxs-lookup"><span data-stu-id="89e82-p105">The key step in this command is specifying which customer to access for the reporting information. You do this in the  _ConnectionURI_ parameter, where you provide the FQDN of the initial domain name as the value to the _DelegatedOrg_ parameter. This tells remote Windows PowerShell for Exchange Online PowerShell remote Windows PowerShell the endpoint to connect to. remote Windows PowerShell must connect to Office 365 reporting in the context of a specific customer each time a report is run. After this customer is specified, all of the following commands are run in the context of that customer. This lets the partner to access all the available reports for this customer.</span></span>
    
3. <span data-ttu-id="89e82-137">Ejecute el comando siguiente.</span><span class="sxs-lookup"><span data-stu-id="89e82-137">Run the following command.</span></span>
    
  ```
  Import-PSSession $Session
  ```

> [!NOTE]
> <span data-ttu-id="89e82-p106">Hay un límite de tres sesiones simultáneas que se pueden ejecutar en una cuenta. Asegúrese de desconectarse de la sesión remota de Windows PowerShell cuando haya finalizado. Si cierra la ventana de Windows PowerShell sin desconectar la sesión, podría agotar todas las sesiones de Windows PowerShell remotas que tenga disponibles y deberá esperar a que las sesiones expiren. Ejecute el siguiente comando para desconectar la sesión remota de Windows PowerShell. >  `Remove-PSSession $Session`</span><span class="sxs-lookup"><span data-stu-id="89e82-p106">There is a limit of three simultaneous sessions that can run under one account. Be sure to disconnect the remote Windows PowerShell session when you're finished. If you close the Windows PowerShell window without disconnecting the session, you can use up all the remote Windows PowerShell sessions available to you, and you'll need to wait for the sessions to expire. To disconnect the remote Windows PowerShell session, run the following command. >  `Remove-PSSession $Session`</span></span>
  
## <a name="how-do-you-know-this-worked"></a><span data-ttu-id="89e82-142">¿Cómo saber si el proceso se ha completado correctamente?</span><span class="sxs-lookup"><span data-stu-id="89e82-142">How do you know this worked?</span></span>

<span data-ttu-id="89e82-p107">Después del paso 3, los cmdlets de Exchange Online se importan a la sesión local de Windows PowerShell, como se indica en una barra de progreso. Si no aparece ningún error, la conexión se habrá establecido correctamente. Una prueba rápida es ejecutar un cmdlet de Exchange Online(por ejemplo, **Get-Mailbox** ) y ver los resultados.</span><span class="sxs-lookup"><span data-stu-id="89e82-p107">After Step 3, the Exchange Online cmdlets are imported into your local Windows PowerShell session as tracked by a progress bar. If you don't receive any errors, you connected successfully. A quick test is to run an Exchange Online cmdlet—for example, **Get-Mailbox** —and see the results.</span></span>
  
<span data-ttu-id="89e82-146">Si surgen errores, compruebe los siguientes requisitos:</span><span class="sxs-lookup"><span data-stu-id="89e82-146">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="89e82-p108">Un problema habitual es una contraseña incorrecta. Vuelva a realizar los tres pasos y preste especial atención al nombre de usuario y contraseña que escriba en el paso 1.</span><span class="sxs-lookup"><span data-stu-id="89e82-p108">A common problem is an incorrect password. Run the three steps again and pay close attention to the user name and password you enter in Step 1.</span></span>
    
- <span data-ttu-id="89e82-149">Para evitar que se produzcan ataques por denegación de servicio (DoS), solo se pueden tener abiertas tres conexiones remotas de Windows PowerShell a la organización de Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="89e82-149">To help prevent denial-of-service (DoS) attacks, you're limited to three open remote Windows PowerShell connections to your Exchange Online organization.</span></span>
    
- <span data-ttu-id="89e82-p109">Windows PowerShell debe estar configurado para ejecutar scripts. Esta opción se configura una sola vez en el equipo, y no cada vez que se conecte. Para permitir que Windows PowerShell ejecute scripts firmados, ejecute el siguiente comando en una ventana de Windows PowerShell elevada (una ventana de Windows PowerShell que abrió cuando seleccionó **Ejecutar como administrador**).</span><span class="sxs-lookup"><span data-stu-id="89e82-p109">Windows PowerShell needs to be configured to run scripts. You need to configure this setting only once on your computer, not every time you connect. To enable Windows PowerShell to run signed scripts, run the following command in an elevated Windows PowerShell window (a Windows PowerShell window you opened by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

- <span data-ttu-id="89e82-p110">La cuenta que use para conectarse a Exchange Online debe estar habilitada para Windows PowerShell remoto. Para más información consulte [Administrar el acceso a PowerShell remoto en Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534018).</span><span class="sxs-lookup"><span data-stu-id="89e82-p110">The account you use to connect to Exchange Online must be enabled for remote Windows PowerShell. For more information, see [Manage Remote PowerShell Access in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534018).</span></span>
    
- <span data-ttu-id="89e82-p111">Debe abrir el tráfico del puerto TCP 80 entre su equipo local y Exchange Online. Probablemente esté abierta, pero es un aspecto que se debe tener en cuenta si la directiva de acceso a Internet de su organización es restrictiva.</span><span class="sxs-lookup"><span data-stu-id="89e82-p111">TCP port 80 traffic needs to be open between your local computer and Exchange Online. It's probably open, but it's something to consider if your organization has a restrictive Internet access policy.</span></span>
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a><span data-ttu-id="89e82-157">Llamar directamente al cmdlet con Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="89e82-157">Call the cmdlet directly with Invoke-Command</span></span>

<span data-ttu-id="89e82-p112">Importar una sesión remota de Windows PowerShell puede ser un proceso largo, ya que incorpora todos los cmdlets de Exchange Online. Esto puede ser un problema para el procesamiento por lotes, por ejemplo, cuando se ejecutan informes o se realizan cambios masivos para diferentes inquilinos. Como alternativa al uso de **Import-PSSession**, puede llamar a los cmdlets que desea usar directamente con **Invoke-Command**. Por ejemplo, para llamar al cmdlet **get-mailbox**, reemplace esta sintaxis por `Import-PSSession $Session`.</span><span class="sxs-lookup"><span data-stu-id="89e82-p112">Importing a remote Windows PowerShell session can be a lengthy process because it brings in all Exchange Online cmdlets. This can be an issue in batch processing—for example, when you are running reports or making bulk changes for different tenants. As an alternative to using **Import-PSSession**, you can call cmdlets you want to use directly with **Invoke-Command**. For example, to call the **get-mailbox** cmdlet, substitute this syntax for `Import-PSSession $Session`.</span></span>
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a><span data-ttu-id="89e82-162">Más cmdlets de informes</span><span class="sxs-lookup"><span data-stu-id="89e82-162">More reporting cmdlets</span></span>

<span data-ttu-id="89e82-p113">Los cmdlets que se usan en este tema son cmdlets de Windows PowerShell. Para obtener más información sobre estos cmdlets, consulte los siguientes temas:</span><span class="sxs-lookup"><span data-stu-id="89e82-p113">The cmdlets that you used in this topic are Windows PowerShell cmdlets. For more information about these cmdlets, see the following topics:</span></span>
  
- [<span data-ttu-id="89e82-165">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="89e82-165">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
    
- [<span data-ttu-id="89e82-166">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="89e82-166">New-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389621)
    
- [<span data-ttu-id="89e82-167">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="89e82-167">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389619)
    
- [<span data-ttu-id="89e82-168">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="89e82-168">Remove-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389620)
    
- [<span data-ttu-id="89e82-169">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="89e82-169">Set-ExecutionPolicy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389623)
    

