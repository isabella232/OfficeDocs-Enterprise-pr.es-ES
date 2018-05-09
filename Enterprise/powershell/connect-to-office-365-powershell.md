---
title: Conectarse a PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: 'Resumen: Conéctese a la organización de Office 365 con Office 365 PowerShell para realizar tareas de centro de administración de la línea de comandos.'
ms.openlocfilehash: eac56ae28ab48bb53842725d703bf81fb37d31eb
ms.sourcegitcommit: def3e311db9322e469753bac59ff03624349b140
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/09/2018
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="586c3-103">Conectarse a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="586c3-103">Connect to Office 365 PowerShell</span></span>

 <span data-ttu-id="586c3-104">**Resumen:** Conectarse a la organización de Office 365 con Office 365 PowerShell para realizar tareas de administración desde la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="586c3-104">**Summary:** Connect to your Office 365 organization using Office 365 PowerShell to perform administration tasks from the command line.</span></span>
  
<span data-ttu-id="586c3-p101">Con PowerShell de Office 365, se puede configurar Office 365 desde la línea de comandos. Conectarse a PowerShell de Office 365 es un sencillo proceso de tres pasos con el que instalará el software, ejecutará el software necesario y, después, se conectará a la organización de Office 365.</span><span class="sxs-lookup"><span data-stu-id="586c3-p101">Office 365 PowerShell lets you to manage your Office 365 settings from the command line. Connecting to Office 365 PowerShell is a simple three-step process where you install the required software, run the required software, and then connect to your Office 365 organization.</span></span> 

  
> [!TIP]
> <span data-ttu-id="586c3-p102">**¿Es la primera vez que usa PowerShell?** Vea el [vídeo de información general sobre PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx) ofrecido por LinkedIn Learning.</span><span class="sxs-lookup"><span data-stu-id="586c3-p102">**New to PowerShell?** See a [video Overview of PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), brought to you by LinkedIn Learning.</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="586c3-109">¿Qué necesita saber antes de comenzar?</span><span class="sxs-lookup"><span data-stu-id="586c3-109">What do you need to know before you begin?</span></span>

- <span data-ttu-id="586c3-110">Tiempo estimado para finalizar: 5 minutos</span><span class="sxs-lookup"><span data-stu-id="586c3-110">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="586c3-111">Puede usar las siguientes versiones de Windows:</span><span class="sxs-lookup"><span data-stu-id="586c3-111">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="586c3-112">Windows 10, Windows 8.1, Windows 8 o Windows 7 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="586c3-112">Windows 10, Windows 8.1, Windows 8 or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="586c3-113">Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 o Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="586c3-113">Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>
    
    > [!NOTE]
    ><span data-ttu-id="586c3-p103">Use una versión de 64 bits de Windows. La compatibilidad con la versión de 32 bits de Módulo de Microsoft Azure Active Directory para Windows PowerShell se descontinuó en octubre de 2014.</span><span class="sxs-lookup"><span data-stu-id="586c3-p103">Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
-  <span data-ttu-id="586c3-p104">Estos procedimientos están diseñados para los usuarios que son miembros de un rol de administración de Office 365. Para obtener más información, vea [roles de administrador acerca de Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="586c3-p104">These procedures are intended for users who are members of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="586c3-118">Conectar con el Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="586c3-118">Connect with the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="586c3-119">Los comandos del Módulo Microsoft Azure Active Directory para Windows PowerShell tienen **Msol** en el nombre de su cmdlet.</span><span class="sxs-lookup"><span data-stu-id="586c3-119">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="586c3-120">Paso 1: Instalar el software necesario</span><span class="sxs-lookup"><span data-stu-id="586c3-120">Step 1: Install required software</span></span>

<span data-ttu-id="586c3-p105">Estos pasos son necesarios una sola vez en el equipo, no cada vez que se conecta. Sin embargo, probablemente necesitará instalar las versiones más recientes de software periódicamente.</span><span class="sxs-lookup"><span data-stu-id="586c3-p105">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="586c3-123">Instale la versión de 64 bits de Microsoft Online Services - Ayudante para el inicio de sesión: [Ayudante para el inicio de sesión de Microsoft Online Services para profesionales de TI (RTW)](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span><span class="sxs-lookup"><span data-stu-id="586c3-123">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="586c3-124">Instale el Módulo Microsoft Azure Active Directory para Windows PowerShell siguiendo estos pasos:</span><span class="sxs-lookup"><span data-stu-id="586c3-124">Install the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="586c3-125">Abra un símbolo del sistema de PowerShell con permisos de administrador.</span><span class="sxs-lookup"><span data-stu-id="586c3-125">Open an administrator-level PowerShell command prompt.</span></span>
  - <span data-ttu-id="586c3-126">Ejecute el comando **Install-Module MSOnline**.</span><span class="sxs-lookup"><span data-stu-id="586c3-126">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="586c3-127">Si se le pide que instale el proveedor de NuGet, escriba **Y** y presione ENTRAR.</span><span class="sxs-lookup"><span data-stu-id="586c3-127">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="586c3-128">Si se le pide que instale el módulo desde PSGallery, escriba **Y** y presione ENTRAR.</span><span class="sxs-lookup"><span data-stu-id="586c3-128">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="586c3-129">Después de la instalación, cierre la ventana de comandos de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="586c3-129">After installation, close the PowerShell command window.</span></span>
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="586c3-130">Paso 2: Conectarse a Azure AD para su suscripción de Office 365</span><span class="sxs-lookup"><span data-stu-id="586c3-130">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="586c3-131">Para conectarse solo con el *nombre de cuenta y la contraseña*:</span><span class="sxs-lookup"><span data-stu-id="586c3-131">To connect with just an *account name and password*:</span></span>
  
1. <span data-ttu-id="586c3-132">Ejecute un símbolo del sistema de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="586c3-132">Run a Windows PowerShell command prompt.</span></span>
2. <span data-ttu-id="586c3-133">En la ventana de comandos de **Windows PowerShell**, ejecute los comandos siguientes:</span><span class="sxs-lookup"><span data-stu-id="586c3-133">In the **Windows PowerShell** command window, run the following commands:</span></span>
    
```
$UserCredential = Get-Credential
Connect-MsolService -Credential $UserCredential
```

3. <span data-ttu-id="586c3-134">En el cuadro de diálogo **Solicitud de credenciales para Windows PowerShell**, escriba su nombre de usuario y contraseña de Office 365cuenta profesional o educativa y, luego, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="586c3-134">In the **Windows PowerShell Credential Request** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>
    
<span data-ttu-id="586c3-135">Para conectarse mediante la *autenticación multifactor (MFA)*:</span><span class="sxs-lookup"><span data-stu-id="586c3-135">To connect with *multi-factor authentication (MFA)*:</span></span>
  
1. <span data-ttu-id="586c3-136">Ejecute un símbolo del sistema de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="586c3-136">Run a Windows PowerShell command prompt.</span></span>
2. <span data-ttu-id="586c3-137">Ejecute el comando siguiente en la ventana de comandos del **Módulo Microsoft Azure Active Directory para Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="586c3-137">In the **Microsoft Azure Active Directory Module for Windows PowerShell** command window, run the following command.</span></span>
    
```
Connect-MsolService
```

3. <span data-ttu-id="586c3-138">En el cuadro de diálogo **Azure Active Directory PowerShell**, escriba su nombre de usuario y contraseña de Office 365cuenta profesional o educativa y, a continuación, haga clic en **Iniciar sesión**.</span><span class="sxs-lookup"><span data-stu-id="586c3-138">In the **Azure Active Directory PowerShell** dialog box, type your Office 365 work or school account user name and password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="586c3-139">Siga las instrucciones del cuadro de diálogo de **Azure Active Directory PowerShell** para proporcionar información de autenticación adicional, como un código de comprobación, y haga clic en **Iniciar sesión**.</span><span class="sxs-lookup"><span data-stu-id="586c3-139">Follow the instructions in the **Azure Active Directory PowerShell** dialog box to provide additional authentication information, such as a verification code, and then click **Sign in**.</span></span>
    
### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="586c3-140">¿Cómo saber si el proceso se ha completado correctamente?</span><span class="sxs-lookup"><span data-stu-id="586c3-140">How do you know this worked?</span></span>

<span data-ttu-id="586c3-p106">Si no se muestra ningún error, la conexión se habrá establecido correctamente. Para hacer una prueba rápida, ejecute un cmdlet de Office 365, como **Get-MsolUser**, y vea los resultados.</span><span class="sxs-lookup"><span data-stu-id="586c3-p106">If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="586c3-143">Si surgen errores, compruebe los siguientes requisitos:</span><span class="sxs-lookup"><span data-stu-id="586c3-143">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="586c3-p107">**Un problema habitual es una contraseña incorrecta**. Vuelva a realizar el paso 3 y preste especial atención al nombre de usuario y la contraseña que escriba.</span><span class="sxs-lookup"><span data-stu-id="586c3-p107">**A common problem is an incorrect password**. Run Step 3 again. and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="586c3-p108">**El Módulo de Microsoft Azure Active Directory para Windows PowerShell requiere que la característica Microsoft .NET Framework 3.5.* x* esté habilitada en el equipo**. Es probable que el equipo tenga instalada una versión más reciente (por ejemplo, 4 o 4.5. *x*), pero sea posible habilitar o deshabilitar la compatibilidad con versiones anteriores de .NET Framework. Para obtener más información al respecto, consulte los temas siguientes:</span><span class="sxs-lookup"><span data-stu-id="586c3-p108">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5.* x* feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.* x*), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled. For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="586c3-149">Para Windows Server 2012 o Windows Server 2012 R2, vea [Habilitar .NET Framework 3.5 con el Asistente para agregar roles y características](https://go.microsoft.com/fwlink/p/?LinkId=532368).</span><span class="sxs-lookup"><span data-stu-id="586c3-149">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="586c3-150">Para Windows 8 o Windows 8.1, vea [Instalar .NET Framework 3.5 en Windows 8 u 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369).</span><span class="sxs-lookup"><span data-stu-id="586c3-150">For Windows 8 or Windows 8.1, see [Installing the .NET Framework 3.5 on Windows 8 or 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)</span></span>
    
  - <span data-ttu-id="586c3-151">Para Windows 7 o Windows Server 2008 R2, vea [No puede abrir el Módulo de Azure Active Directory para Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370).</span><span class="sxs-lookup"><span data-stu-id="586c3-151">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>
    
- <span data-ttu-id="586c3-p109">**Puede que su versión de Módulo de Microsoft Azure Active Directory para Windows PowerShell esté obsoleta.** Para comprobarlo, ejecute el siguiente comando en PowerShell de Office 365 o Módulo de Microsoft Azure Active Directory para Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="586c3-p109">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="586c3-154">Si el número de versión devuelto es menor que el valor 1.0.8070.2, desinstale el Módulo de Microsoft Azure Active Directory para Windows PowerShell e instale la versión más reciente desde el vínculo en el paso 1.</span><span class="sxs-lookup"><span data-stu-id="586c3-154">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="586c3-155">**Si recibe un error de conexión, vea este tema:** [Error “Connect-MsolService: Se produjo una excepción de tipo”](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span><span class="sxs-lookup"><span data-stu-id="586c3-155">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    
<span data-ttu-id="586c3-156"><a name="ConnectV2"> </a></span><span class="sxs-lookup"><span data-stu-id="586c3-156"></span></span>
## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="586c3-157">Conectar con Azure Active Directory PowerShell para el módulo de gráfico</span><span class="sxs-lookup"><span data-stu-id="586c3-157">Connect with the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="586c3-158">Comandos en el módulo [Azure Active Directory PowerShell para el módulo de gráfico](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) tienen **AzureAD** en su nombre de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="586c3-158">Commands in the [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) module have **AzureAD** in their cmdlet name.</span></span>

<span data-ttu-id="586c3-159">Para conocer los procedimientos que requieren los nuevos cmdlets en Azure Active Directory PowerShell para el módulo de gráfico, siga estos pasos para instalar el módulo y conectarlo a su suscripción de Office 365.</span><span class="sxs-lookup"><span data-stu-id="586c3-159">For procedures that require the new cmdlets in the Azure Active Directory PowerShell for Graph module, use these steps to install the module and connect to your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="586c3-160">Para obtener información acerca de la compatibilidad con diferentes versiones de Microsoft Windows, vea [Windows Azure Active Directory PowerShell para el módulo de gráfico](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) .</span><span class="sxs-lookup"><span data-stu-id="586c3-160">See [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) for information about the support for different versions of Microsoft Windows.</span></span>
>

### <a name="step-1-install-required-software"></a><span data-ttu-id="586c3-161">Paso 1: Instalar el software necesario</span><span class="sxs-lookup"><span data-stu-id="586c3-161">Step 1: Install required software</span></span>

<span data-ttu-id="586c3-p110">Estos pasos son necesarios una sola vez en el equipo, no cada vez que se conecta. Sin embargo, probablemente necesitará instalar las versiones más recientes de software periódicamente.</span><span class="sxs-lookup"><span data-stu-id="586c3-p110">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>

  
1. <span data-ttu-id="586c3-164">Abra un símbolo del sistema de Windows PowerShell con privilegios elevados (ejecute Windows PowerShell como administrador).</span><span class="sxs-lookup"><span data-stu-id="586c3-164">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="586c3-165">En la ventana de comandos **Administrador: Windows PowerShell**, ejecute este comando:</span><span class="sxs-lookup"><span data-stu-id="586c3-165">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```
  Install-Module -Name AzureAD 
  ```

<span data-ttu-id="586c3-166">Si se le pregunta si quiere instalar un módulo desde un repositorio que no es de confianza, escriba **Y** y presione ENTRAR.</span><span class="sxs-lookup"><span data-stu-id="586c3-166">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>


### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="586c3-167">Paso 2: Conectarse a Azure AD para su suscripción de Office 365</span><span class="sxs-lookup"><span data-stu-id="586c3-167">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="586c3-168">Para conectarse a su suscripción de Office 365 mediante el *nombre de cuenta y la contraseña*:</span><span class="sxs-lookup"><span data-stu-id="586c3-168">To connect to your Office 365 subscription with an *account name and password*:</span></span>
    
```
$UserCredential = Get-Credential
Connect-AzureAD -Credential $UserCredential
```

<span data-ttu-id="586c3-169">En el cuadro de diálogo **Solicitud de credenciales para Windows PowerShell**, escriba su nombre de usuario y contraseña de Office 365cuenta profesional o educativa y, luego, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="586c3-169">In the **Windows PowerShell Credential Request** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>
    
<span data-ttu-id="586c3-170">Para conectarse a su suscripción de Office 365 mediante la *autenticación multifactor (MFA)*:</span><span class="sxs-lookup"><span data-stu-id="586c3-170">To connect to your Office 365 subscription with *multi-factor authentication (MFA)*:</span></span>

```
Connect-AzureAD
```

<span data-ttu-id="586c3-171">En el cuadro de diálogo **Azure Active Directory PowerShell**, escriba su nombre de usuario y contraseña de Office 365cuenta profesional o educativa y, a continuación, haga clic en **Iniciar sesión**.</span><span class="sxs-lookup"><span data-stu-id="586c3-171">In the **Azure Active Directory PowerShell** dialog box, type your Office 365 work or school account user name and password, and then click **Sign in**.</span></span>
    
<span data-ttu-id="586c3-172">Siga las instrucciones del cuadro de diálogo de **Azure Active Directory PowerShell** para proporcionar información de autenticación adicional, como un código de comprobación, y haga clic en **Iniciar sesión**.</span><span class="sxs-lookup"><span data-stu-id="586c3-172">Follow the instructions in the **Azure Active Directory PowerShell** dialog box to provide additional authentication information, such as a verification code, and then click **Sign in**.</span></span>
    
<span data-ttu-id="586c3-173">Después de conectar, puede usar los cmdlets de nuevo para el [Azure Active Directory PowerShell para el módulo de gráfico](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span><span class="sxs-lookup"><span data-stu-id="586c3-173">After connecting, you can use the new cmdlets for the [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="586c3-174">Consulte también</span><span class="sxs-lookup"><span data-stu-id="586c3-174">See also</span></span>

- [<span data-ttu-id="586c3-175">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="586c3-175">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="586c3-176">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="586c3-176">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="586c3-177">Conectarse a todos los servicios de Office 365 en una sola ventana de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="586c3-177">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [<span data-ttu-id="586c3-178">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="586c3-178">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [<span data-ttu-id="586c3-179">Connect-MsolService</span><span class="sxs-lookup"><span data-stu-id="586c3-179">Connect-MsolService</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532375)

