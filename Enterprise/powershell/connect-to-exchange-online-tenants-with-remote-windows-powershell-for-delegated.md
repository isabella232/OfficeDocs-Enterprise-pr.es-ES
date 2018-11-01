---
title: Conectarse a los inquilinos de Exchange Online con el modo remoto de Windows PowerShell para asociados con permiso de acceso delegado (DAP)
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: ae5f1a87-8b77-4f93-a1b8-56f800aeb283
description: 'Resumen: use el modo remoto de Windows PowerShell para conectarse a Exchange Online con el valor DelegatedOrg.'
ms.openlocfilehash: d14726a2983bf3f2d569305e1a7e2e1a86811ff5
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849906"
---
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="a4c10-103">Conectarse a los inquilinos de Exchange Online con el modo remoto de Windows PowerShell para asociados con permiso de acceso delegado (DAP)</span><span class="sxs-lookup"><span data-stu-id="a4c10-103">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="a4c10-104">**Resumen:** use el modo remoto de PowerShell para conectarse a Exchange Online con el valor `DelegatedOrg`.</span><span class="sxs-lookup"><span data-stu-id="a4c10-104">**Summary:** Use remote Windows PowerShell to connect to Exchange Online by using the `DelegatedOrg` parameter.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a4c10-p101">Los procedimientos descritos en este tema son solo para partners con permiso de acceso delegado (DAP). Si no es un partner con DAP, no use los procedimientos descritos en este tema.</span><span class="sxs-lookup"><span data-stu-id="a4c10-p101">The procedures in this topic are only for Delegated Access Permission (DAP) partners. If you aren't a DAP partner, don't use the procedures in this topic.</span></span> 
  
<span data-ttu-id="a4c10-p102">Los partners con DAP son partners proveedores de soluciones en la nube de Microsoft (CSP) y redifusión web. Generalmente son proveedores de red o de telecomunicaciones para otras compañías. Empaquetan suscripciones en sus ofertas de servicio a sus clientes. Poseen un arrendamiento de asociado al que se le conceden automáticamente permisos Administrar en nombre de (AOBO) para sus arrendamientos de cliente de Office 365, de modo que pueden administrar todos sus arrendamientos de cliente e informar al respecto.</span><span class="sxs-lookup"><span data-stu-id="a4c10-p102">DAP partners are Syndication and Cloud Solution Providers (CSP) partners. They are frequently network or telecom providers to other companies. They bundle subscriptions into their service offerings to their customers. They own a partner tenancy that is automatically granted Administer On Behalf Of (AOBO) permissions to their Office 365customer tenancies so they can administer and report on all of their customer tenancies.</span></span>

<span data-ttu-id="a4c10-p103">Los partners con DAP pueden usar Exchange Online PowerShell para administrar la configuración de Exchange Online y obtener informes de Office 365 desde la línea de comandos. Use la sesión de Windows PowerShell en su equipo local para crear una sesión remota de PowerShell en Exchange Online. Es un sencillo proceso de tres pasos que consiste en escribir las credenciales, proporcionar la configuración de conexión necesaria y, después, importar los cmdlets de Exchange Online en la sesión local de Windows PowerShell para poder usarlos.</span><span class="sxs-lookup"><span data-stu-id="a4c10-p103">Remote PowerShell allows you to manage your Exchange Online settings from the command line. You use Windows PowerShell on your local computer to create a remote Shell session to Exchange Online. It’s a simple three-step process where you enter your Exchange Online credentials, provide the required connection settings, and then import the Exchange Online cmdlets into your local Windows PowerShell session so that you can use them.</span></span>

> [!NOTE]
> <span data-ttu-id="a4c10-p104">Los partners con DAP no pueden usar los procedimientos descritos en [Conectarse a Exchange Online PowerShell con la autenticación multifactor](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell) para conectarse a sus organizaciones de espacios empresariales de clientes en Exchange Online PowerShell. MFA y el módulo remoto Exchange Online PowerShell no funcionan con la autenticación delegada.</span><span class="sxs-lookup"><span data-stu-id="a4c10-p104">DAP partners can't use the procedures in [Connect to Exchange Online PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell) to connect to their customer tenant organizations in Exchange Online PowerShell. MFA and the Exchange Online Remote PowerShell Module don't work with delegated authentication.</span></span>
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="a4c10-116">¿Qué necesita saber antes de comenzar?</span><span class="sxs-lookup"><span data-stu-id="a4c10-116">What do you need to know before you begin?</span></span>

- <span data-ttu-id="a4c10-117">Tiempo estimado para finalizar: 5 minutos</span><span class="sxs-lookup"><span data-stu-id="a4c10-117">Estimated time to complete: 5 minutes</span></span>

- <span data-ttu-id="a4c10-118">Puede usar las siguientes versiones de Windows:</span><span class="sxs-lookup"><span data-stu-id="a4c10-118">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="a4c10-119">Windows 10</span><span class="sxs-lookup"><span data-stu-id="a4c10-119">Windows 10</span></span>

  - <span data-ttu-id="a4c10-120">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="a4c10-120">Windows 8.1</span></span>

  - <span data-ttu-id="a4c10-121">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="a4c10-121">Windows Server 2016</span></span>

  - <span data-ttu-id="a4c10-122">Windows Server 2012 o Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="a4c10-122">Windows Server 2012 or Windows Server 2012 R2</span></span>

  - <span data-ttu-id="a4c10-123">Windows 7 Service Pack 1 (SP1)<sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="a4c10-123">Windows 7 Service Pack 1 (SP1)\*</span></span>

  - <span data-ttu-id="a4c10-124">Windows Server 2008 R2 SP1<sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="a4c10-124">Windows Server 2008 R2 SP1</span></span>

    <span data-ttu-id="a4c10-p105"><sup>\*</sup> Para versiones anteriores de Windows, deberá instalar Microsoft.NET Framework 4.5 o una versión posterior y, a continuación, una versión actualizada de Windows Management Framework: 3.0, 4.0 o 5.1 (solamente uno). Para obtener más información, vea [Instalación de .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868), [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757), [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344) y [Windows Management Framework 5.1](https://aka.ms/wmf5download).</span><span class="sxs-lookup"><span data-stu-id="a4c10-p105"><sup>\*</sup> For older versions of Windows, you need to install the Microsoft.NET Framework 4.5 or later and then an updated version of the Windows Management Framework: 3.0, 4.0, or 5.1 (only one). For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868), [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757), [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344), and [Windows Management Framework 5.1](https://aka.ms/wmf5download).</span></span>

- <span data-ttu-id="a4c10-p106">Windows PowerShell se debe configurar para ejecutar scripts y, por defecto, no lo está. Obtendrá el siguiente error al intentar conectar:</span><span class="sxs-lookup"><span data-stu-id="a4c10-p106">Windows_PowerShell needs to be configured to run scripts, and by default, it isn't. You get the following error when you try to connect:</span></span>

  `Files cannot be loaded because running scripts is disabled on this system. Provide a valid certificate with which to sign the files.`

  <span data-ttu-id="a4c10-129">Para requerir que todos los scripts de PowerShell que se descargue de internet sean de publicadores de confianza, ejecute el siguiente comando en una ventana de Windows PowerShell con permisos elevados (o sea, una ventana de Windows PowerShell que se abre seleccionando **Ejecutar como administrador**):</span><span class="sxs-lookup"><span data-stu-id="a4c10-129">To require all PowerShell scripts that you download from the internet are signed by a trusted publisher, run the following command in an elevated Windows PowerShell window (a Windows PowerShell window you open by selecting **Run as administrator**):</span></span>

    ```
    Set-ExecutionPolicy RemoteSigned
    ```

  <span data-ttu-id="a4c10-130">Esta opción se configura una sola vez en el equipo, y no cada vez que se conecte.</span><span class="sxs-lookup"><span data-stu-id="a4c10-130">You need to configure this setting only once on your computer, not every time you connect.</span></span>

- <span data-ttu-id="a4c10-131">Para obtener información acerca de los métodos abreviados de teclado que se pueden aplicar a los procedimientos de este tema, consulte [Métodos abreviados de teclado en el Centro de administración de Exchange](https://go.microsoft.com/fwlink/p/?LinkId=534017).</span><span class="sxs-lookup"><span data-stu-id="a4c10-131">For information about keyboard shortcuts that might apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](https://go.microsoft.com/fwlink/p/?LinkId=534017).</span></span>

## <a name="connect-to-exchange-online-for-customer-organizations"></a><span data-ttu-id="a4c10-132">Conectarse a Exchange Online para organizaciones de cliente</span><span class="sxs-lookup"><span data-stu-id="a4c10-132">Connect to Exchange Online for customer organizations</span></span>

1. <span data-ttu-id="a4c10-133">En el equipo local, abra Windows PowerShell y ejecute el siguiente comando.</span><span class="sxs-lookup"><span data-stu-id="a4c10-133">On your local computer, open Windows PowerShell and run the following command.</span></span>
    
    ```
    $UserCredential = Get-Credential
    ```

    <span data-ttu-id="a4c10-134">En el cuadro de diálogo **Solicitud de credenciales para Windows PowerShell**, escriba su nombre de usuario de administrador DAP y contraseña y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="a4c10-134">In the **Windows PowerShell Credential Request** dialog box, enter your DAP administrator user name and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="a4c10-135">Reemplace _\<nombre de dominio de espacio empresarial de cliente\>_ con el nombre de dominio del espacio empresarial al que desee conectarse y ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="a4c10-135">Replace _\<customer tenant domain name\>_ with the name of the tenant domain that you want to connect to, and run the following command:</span></span>
    
    ```
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name> -Credential $UserCredential -Authentication Basic -AllowRedirection
    ```

    <span data-ttu-id="a4c10-p107">El paso clave en este comando es especificar a qué cliente hay que acceder para obtener los datos de informes. Esto se realiza en el parámetro _ConnectionURI_, donde se proporciona el FQDN del nombre de dominio inicial como el valor para `?DelegatedOrg=`. Este valor indica el punto final de Exchange Online PowerShell al que conectarse. PowerShell remoto debe conectarse a los informes de Office 365 en el contexto de un cliente específico cada vez que un informe se ejecuta. Después de conectarse a Exchange Online PowerShell, todos los comandos siguientes se ejecutan en el contexto de dicho cliente, lo que permite acceder a todos los informes disponibles para este cliente.</span><span class="sxs-lookup"><span data-stu-id="a4c10-p107">The key step in this command is specifying which customer to access for the reporting information. You do this in the  _ConnectionURI_ parameter, where you provide the FQDN of the initial domain name as the value to the `?DelegatedOrg=` parameter. This tells remote Windows PowerShell for Exchange Online PowerShell remote Windows PowerShell the endpoint to connect to. remote Windows PowerShell must connect to Office 365 reporting in the context of a specific customer each time a report is run. After this customer is specified, all of the following commands are run in the context of that customer. This lets the partner to access all the available reports for this customer.</span></span>
    
3. <span data-ttu-id="a4c10-141">Ejecute el comando siguiente.</span><span class="sxs-lookup"><span data-stu-id="a4c10-141">Run the following command.</span></span>
    
    ```
    Import-PSSession $Session
    ```

> [!NOTE]
> <span data-ttu-id="a4c10-p108">Hay un límite de tres sesiones simultáneas que se pueden ejecutar en una cuenta. Asegúrese de desconectarse de la sesión remota de PowerShell cuando haya finalizado. Si cierra la ventana de Windows PowerShell sin desconectar la sesión, podría agotar todas las sesiones de PowerShell remotas que tenga disponibles y deberá esperar a que las sesiones expiren. Ejecute el siguiente comando para desconectar la sesión remota de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="a4c10-p108">There is a limit of three simultaneous sessions that can run under one account. Be sure to disconnect the remote Windows PowerShell session when you're finished. If you close the Windows PowerShell window without disconnecting the session, you can use up all the remote Windows PowerShell sessions available to you, and you'll need to wait for the sessions to expire. To disconnect the remote Windows PowerShell session, run the following command. >  </span></span>

```
Remove-PSSession $Session
```
  
## <a name="how-do-you-know-this-worked"></a><span data-ttu-id="a4c10-146">¿Cómo saber si el proceso se ha completado correctamente?</span><span class="sxs-lookup"><span data-stu-id="a4c10-146">How do you know this worked?</span></span>

<span data-ttu-id="a4c10-p109">Después del paso 3, los cmdlets de Exchange Online se importan a la sesión local de Windows PowerShell, como se indica en una barra de progreso. Si no aparece ningún error, la conexión se habrá establecido correctamente. Una prueba rápida es ejecutar un cmdlet de Exchange Online (por ejemplo, **Get-Mailbox**) y ver los resultados.</span><span class="sxs-lookup"><span data-stu-id="a4c10-p109">After Step 3, the Exchange Online cmdlets are imported into your local Windows PowerShell session as tracked by a progress bar. If you don't receive any errors, you connected successfully. A quick test is to run an Exchange Online cmdlet—for example, **Get-Mailbox** —and see the results.</span></span>
  
<span data-ttu-id="a4c10-150">Si surgen errores, compruebe los siguientes requisitos:</span><span class="sxs-lookup"><span data-stu-id="a4c10-150">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="a4c10-p110">Un problema habitual es una contraseña incorrecta. Vuelva a realizar los tres pasos y preste especial atención al nombre de usuario y contraseña que escriba en el paso 1.</span><span class="sxs-lookup"><span data-stu-id="a4c10-p110">A common problem is an incorrect password. Run the three steps again and pay close attention to the user name and password you enter in Step 1.</span></span>
    
- <span data-ttu-id="a4c10-p111">La cuenta que use para conectarse a Exchange Online debe estar habilitada para PowerShell remoto. Para más información consulte [Activar o desactivar el acceso a Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534018).</span><span class="sxs-lookup"><span data-stu-id="a4c10-p111">The account you use to connect to Exchange Online must be enabled for remote Windows PowerShell. For more information, see [Manage Remote PowerShell Access in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534018).</span></span>
    
- <span data-ttu-id="a4c10-p112">Debe abrir el tráfico del puerto TCP 80 entre su equipo local y Exchange Online. Probablemente esté abierta, pero es un aspecto que se debe tener en cuenta si la directiva de acceso a Internet de su organización es restrictiva.</span><span class="sxs-lookup"><span data-stu-id="a4c10-p112">TCP port 80 traffic needs to be open between your local computer and Exchange Online. It's probably open, but it's something to consider if your organization has a restrictive Internet access policy.</span></span>
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a><span data-ttu-id="a4c10-157">Llamar directamente al cmdlet con Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="a4c10-157">Call the cmdlet directly with Invoke-Command</span></span>

<span data-ttu-id="a4c10-p113">Importar una sesión remota de PowerShell (paso 3) puede ser un proceso largo, ya que incorpora _todos_ los cmdlets de Exchange Online. Esto puede ser un problema para el procesamiento por lotes (por ejemplo, cuando se ejecutan informes o se realizan cambios masivos para diferentes inquilinos). Como alternativa al uso de **Import-PSSession**, puede llamar a los cmdlets que desea usar directamente con **Invoke-Command**. Por ejemplo, para llamar al cmdlet **Get-Milbox**, reemplace esta sintaxis por el comando `Import-PSSession $Session` del paso 3:</span><span class="sxs-lookup"><span data-stu-id="a4c10-p113">Importing a remote Windows PowerShell session can be a lengthy process because it brings in all Exchange Online cmdlets. This can be an issue in batch processing—for example, when you are running reports or making bulk changes for different tenants. As an alternative to using Import-PSSession, you can call cmdlets you want to use directly with Invoke-Command. For example, to call the get-mailbox cmdlet, substitute this syntax for .</span></span>
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a><span data-ttu-id="a4c10-162">Más cmdlets de informes</span><span class="sxs-lookup"><span data-stu-id="a4c10-162">More reporting cmdlets</span></span>

<span data-ttu-id="a4c10-p114">Los cmdlets que se usan en este tema son cmdlets de Windows PowerShell. Para obtener más información sobre estos cmdlets, consulte los siguientes temas:</span><span class="sxs-lookup"><span data-stu-id="a4c10-p114">The cmdlets that you used in this topic are Windows PowerShell cmdlets. For more information about these cmdlets, see the following topics:</span></span>
  
- [<span data-ttu-id="a4c10-165">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="a4c10-165">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
    
- [<span data-ttu-id="a4c10-166">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="a4c10-166">New-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389621)
    
- [<span data-ttu-id="a4c10-167">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="a4c10-167">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389619)
    
- [<span data-ttu-id="a4c10-168">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="a4c10-168">Remove-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389620)
    
- [<span data-ttu-id="a4c10-169">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="a4c10-169">Set-ExecutionPolicy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389623)
    

