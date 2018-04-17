---
title: Conectarse a PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/12/2018
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
description: 'Resumen: conéctese a su organización de Office 365 con PowerShell de Office 365 para realizar tareas del Centro de administración de Office 365 desde la línea de comandos.'
ms.openlocfilehash: 95d1e5717d3fec7f0d3102beb65eebaef28bd6cf
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="624c1-103">Conectarse a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="624c1-103">Connect to Office 365 PowerShell</span></span>

 <span data-ttu-id="624c1-104">**Resumen:** conéctese a su organización de Office 365 con PowerShell de Office 365 para realizar tareas de administración de Office 365 desde la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="624c1-104">**Summary:** Connect to your Office 365 organization using Office 365 PowerShell to perform Office 365 administration tasks from the command line.</span></span>
  
<span data-ttu-id="624c1-p101">Con PowerShell de Office 365, se puede configurar Office 365 desde la línea de comandos. Conectarse a PowerShell de Office 365 es un sencillo proceso de tres pasos con el que instalará el software, ejecutará el software necesario y, después, se conectará a la organización de Office 365.</span><span class="sxs-lookup"><span data-stu-id="624c1-p101">Office 365 PowerShell lets you to manage your Office 365 settings from the command line. Connecting to Office 365 PowerShell is a simple three-step process where you install the required software, run the required software, and then connect to your Office 365 organization.</span></span> 

<span data-ttu-id="624c1-107">Tenga en cuenta que estas instrucciones de conexión son las mismas que aparecen en el tema [Azure Active Directory (MSOnline)](https://go.microsoft.com/fwlink/p/?LinkId=528113).</span><span class="sxs-lookup"><span data-stu-id="624c1-107">Note that these connection instructions are the same as those in the topic [Azure ActiveDirectory (MSOnline)](https://go.microsoft.com/fwlink/p/?LinkId=528113).</span></span>
  
> [!TIP]
> <span data-ttu-id="624c1-p102">**¿Es la primera vez que usa PowerShell?** Vea el [vídeo de información general sobre PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx) ofrecido por LinkedIn Learning.</span><span class="sxs-lookup"><span data-stu-id="624c1-p102">**New to PowerShell?** See a [video Overview of PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), brought to you by LinkedIn Learning.</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="624c1-110">¿Qué necesita saber antes de empezar?</span><span class="sxs-lookup"><span data-stu-id="624c1-110">What do you need to know before you begin?</span></span>

- <span data-ttu-id="624c1-111">Tiempo estimado para finalizar: 5 minutos</span><span class="sxs-lookup"><span data-stu-id="624c1-111">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="624c1-112">Puede usar las siguientes versiones de Windows:</span><span class="sxs-lookup"><span data-stu-id="624c1-112">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="624c1-113">Windows 10, Windows 8.1, Windows 8 o Windows 7 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="624c1-113">Windows 10, Windows 8.1, Windows 8 or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="624c1-114">Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 o Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="624c1-114">Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>
    
    > [!NOTE]
    ><span data-ttu-id="624c1-p103">Use una versión de 64 bits de Windows. La compatibilidad con la versión de 32 bits de Módulo de Microsoft Azure Active Directory para Windows PowerShell se descontinuó en octubre de 2014.</span><span class="sxs-lookup"><span data-stu-id="624c1-p103">Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
-  <span data-ttu-id="624c1-p104">Estos procedimientos están destinados a usuarios que son miembros de una función de administración de Office 365. Para obtener más información, consulte [las funciones de administrador acerca de Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="624c1-p104">These procedures are intended for users who are members of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="624c1-119">Conectar con el Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="624c1-119">Connect with the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="624c1-120">Los comandos del Módulo Microsoft Azure Active Directory para Windows PowerShell tienen **Msol** en el nombre de su cmdlet.</span><span class="sxs-lookup"><span data-stu-id="624c1-120">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="624c1-121">Paso 1: Instalar el software necesario</span><span class="sxs-lookup"><span data-stu-id="624c1-121">Step 1: Install required software</span></span>

<span data-ttu-id="624c1-p105">Estos pasos son necesarios una sola vez en el equipo, no cada vez que se conecta. Sin embargo, probablemente necesitará instalar las versiones más recientes de software periódicamente.</span><span class="sxs-lookup"><span data-stu-id="624c1-p105">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="624c1-124">Instale la versión de 64 bits de Microsoft Online Services - Ayudante para el inicio de sesión: [Ayudante para el inicio de sesión de Microsoft Online Services para profesionales de TI (RTW)](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span><span class="sxs-lookup"><span data-stu-id="624c1-124">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="624c1-125">Instale el Módulo Microsoft Azure Active Directory para Windows PowerShell siguiendo estos pasos:</span><span class="sxs-lookup"><span data-stu-id="624c1-125">Install the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="624c1-126">Abra un símbolo del sistema de PowerShell con permisos de administrador.</span><span class="sxs-lookup"><span data-stu-id="624c1-126">Open an administrator-level PowerShell command prompt.</span></span>
  - <span data-ttu-id="624c1-127">Ejecute el comando **Install-Module MSOnline**.</span><span class="sxs-lookup"><span data-stu-id="624c1-127">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="624c1-128">Si se le pide que instale el proveedor de NuGet, escriba **Y** y presione ENTRAR.</span><span class="sxs-lookup"><span data-stu-id="624c1-128">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="624c1-129">Si se le pide que instale el módulo desde PSGallery, escriba **Y** y presione ENTRAR.</span><span class="sxs-lookup"><span data-stu-id="624c1-129">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="624c1-130">Después de la instalación, cierre la ventana de comandos de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="624c1-130">After installation, close the PowerShell command window.</span></span>
    
### <a name="step-2-connect-to-your-office-365-subscription"></a><span data-ttu-id="624c1-131">Paso 2: Conectarse a la suscripción de Office 365</span><span class="sxs-lookup"><span data-stu-id="624c1-131">Step 2: Connect to your Office 365 subscription</span></span>
<span data-ttu-id="624c1-132"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="624c1-132"><a name="step3"> </a></span></span>

<span data-ttu-id="624c1-133">Para conectarse solo con el *nombre de cuenta y la contraseña*:</span><span class="sxs-lookup"><span data-stu-id="624c1-133">To connect with just an *account name and password*:</span></span>
  
1. <span data-ttu-id="624c1-134">Ejecute un símbolo del sistema de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="624c1-134">Run a Windows PowerShell command prompt.</span></span>
2. <span data-ttu-id="624c1-135">En la ventana de comandos de **Windows PowerShell**, ejecute los comandos siguientes:</span><span class="sxs-lookup"><span data-stu-id="624c1-135">In the **Windows PowerShell** command window, run the following commands:</span></span>
    
```
$UserCredential = Get-Credential
Connect-MsolService -Credential $UserCredential
```

3. <span data-ttu-id="624c1-136">En el cuadro de diálogo **Solicitud de credenciales para Windows PowerShell**, escriba su nombre de usuario y contraseña de Office 365cuenta profesional o educativa y, luego, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="624c1-136">In the **Windows PowerShell Credential Request** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>
    
<span data-ttu-id="624c1-137">Para conectarse mediante la *autenticación multifactor (MFA)*:</span><span class="sxs-lookup"><span data-stu-id="624c1-137">To connect with *multi-factor authentication (MFA)*:</span></span>
  
1. <span data-ttu-id="624c1-138">Ejecute un símbolo del sistema de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="624c1-138">Run a Windows PowerShell command prompt.</span></span>
2. <span data-ttu-id="624c1-139">Ejecute el comando siguiente en la ventana de comandos del **Módulo Microsoft Azure Active Directory para Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="624c1-139">In the **Microsoft Azure Active Directory Module for Windows PowerShell** command window, run the following command.</span></span>
    
```
Connect-MsolService
```

3. <span data-ttu-id="624c1-140">En el cuadro de diálogo **Azure Active Directory PowerShell**, escriba su nombre de usuario y contraseña de Office 365cuenta profesional o educativa y, a continuación, haga clic en **Iniciar sesión**.</span><span class="sxs-lookup"><span data-stu-id="624c1-140">In the **Azure Active Directory PowerShell** dialog box, type your Office 365 work or school account user name and password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="624c1-141">Siga las instrucciones del cuadro de diálogo de **Azure Active Directory PowerShell** para proporcionar información de autenticación adicional, como un código de comprobación, y haga clic en **Iniciar sesión**.</span><span class="sxs-lookup"><span data-stu-id="624c1-141">Follow the instructions in the **Azure Active Directory PowerShell** dialog box to provide additional authentication information, such as a verification code, and then click **Sign in**.</span></span>
    
### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="624c1-142">¿Cómo saber si el proceso se ha completado correctamente?</span><span class="sxs-lookup"><span data-stu-id="624c1-142">How do you know this worked?</span></span>
<span data-ttu-id="624c1-143"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="624c1-143"><a name="step3"> </a></span></span>

<span data-ttu-id="624c1-p106">Si no se muestra ningún error, la conexión se habrá establecido correctamente. Para hacer una prueba rápida, ejecute un cmdlet de Office 365, como **Get-MsolUser**, y vea los resultados.</span><span class="sxs-lookup"><span data-stu-id="624c1-p106">If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="624c1-146">Si surgen errores, compruebe los siguientes requisitos:</span><span class="sxs-lookup"><span data-stu-id="624c1-146">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="624c1-p107">**Un problema habitual es una contraseña incorrecta**. Vuelva a realizar el paso 3 y preste especial atención al nombre de usuario y la contraseña que escriba.</span><span class="sxs-lookup"><span data-stu-id="624c1-p107">**A common problem is an incorrect password**. Run Step 3 again. and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="624c1-p108">**El Módulo de Microsoft Azure Active Directory para Windows PowerShell requiere que la característica Microsoft .NET Framework 3.5.*x* esté habilitada en el equipo**. Es probable que el equipo tenga instalada una versión más reciente (por ejemplo, 4 o 4.5. *x*), pero sea posible habilitar o deshabilitar la compatibilidad con versiones anteriores de .NET Framework. Para obtener más información al respecto, consulte los temas siguientes:</span><span class="sxs-lookup"><span data-stu-id="624c1-p108">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5.*x* feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.*x*), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled. For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="624c1-152">Para Windows Server 2012 o Windows Server 2012 R2, vea [Habilitar .NET Framework 3.5 con el Asistente para agregar roles y características](https://go.microsoft.com/fwlink/p/?LinkId=532368).</span><span class="sxs-lookup"><span data-stu-id="624c1-152">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="624c1-153">Para Windows 8 o Windows 8.1, vea [Instalar .NET Framework 3.5 en Windows 8 u 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369).</span><span class="sxs-lookup"><span data-stu-id="624c1-153">For Windows 8 or Windows 8.1, see [Installing the .NET Framework 3.5 on Windows 8 or 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)</span></span>
    
  - <span data-ttu-id="624c1-154">Para Windows 7 o Windows Server 2008 R2, vea [No puede abrir el Módulo de Azure Active Directory para Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370).</span><span class="sxs-lookup"><span data-stu-id="624c1-154">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>
    
- <span data-ttu-id="624c1-p109">**Puede que su versión de Módulo de Microsoft Azure Active Directory para Windows PowerShell esté obsoleta.** Para comprobarlo, ejecute el siguiente comando en PowerShell de Office 365 o Módulo de Microsoft Azure Active Directory para Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="624c1-p109">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="624c1-157">Si el número de versión devuelto es menor que el valor 1.0.8070.2, desinstale el Módulo de Microsoft Azure Active Directory para Windows PowerShell e instale la versión más reciente desde el vínculo en el paso 1.</span><span class="sxs-lookup"><span data-stu-id="624c1-157">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="624c1-158">**Si recibe un error de conexión, vea este tema:** [Error “Connect-MsolService: Se produjo una excepción de tipo”](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span><span class="sxs-lookup"><span data-stu-id="624c1-158">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    
## <a name="connect-with-the-azure-active-directory-v2-powershell-module"></a><span data-ttu-id="624c1-159">Conectarse con el módulo de PowerShell Azure Active Directory V2</span><span class="sxs-lookup"><span data-stu-id="624c1-159">Connect with the Azure Active Directory V2 PowerShell module</span></span>
<span data-ttu-id="624c1-160"><a name="ConnectV2"> </a></span><span class="sxs-lookup"><span data-stu-id="624c1-160"><a name="ConnectV2"> </a></span></span>

<span data-ttu-id="624c1-161">Los comandos del módulo de PowerShell Azure Active Directory V2 incluyen "AzureAD" en su nombre de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="624c1-161">Commands in the Azure Active Directory V2 PowerShell module have "AzureAD" in their cmdlet name.</span></span>

<span data-ttu-id="624c1-162">Para los procedimientos que necesitan los nuevos cmdlets del módulo de PowerShell Azure Active Directory V2, siga estos pasos para instalar el módulo y conectarse a su suscripción a Office 365.</span><span class="sxs-lookup"><span data-stu-id="624c1-162">For procedures that require the new cmdlets in the Azure Active Directory V2 PowerShell module, use these steps to install the module and connect to your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="624c1-163">Vea [Módulo de PowerShell Azure Active Directory V2](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) para obtener información sobre la compatibilidad con diferentes versiones de Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="624c1-163">See [Azure Active Directory V2 PowerShell module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) for information about the support for different versions of Microsoft Windows.</span></span>
>

### <a name="step-1-install-required-software"></a><span data-ttu-id="624c1-164">Paso 1: Instalar el software necesario</span><span class="sxs-lookup"><span data-stu-id="624c1-164">Step 1: Install required software</span></span>

<span data-ttu-id="624c1-p110">Estos pasos son necesarios una sola vez en el equipo, no cada vez que se conecta. Sin embargo, probablemente necesitará instalar las versiones más recientes de software periódicamente.</span><span class="sxs-lookup"><span data-stu-id="624c1-p110">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>

  
1. <span data-ttu-id="624c1-167">Abra un símbolo del sistema de Windows PowerShell con privilegios elevados (ejecute Windows PowerShell como administrador).</span><span class="sxs-lookup"><span data-stu-id="624c1-167">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="624c1-168">En la ventana de comandos **Administrador: Windows PowerShell**, ejecute este comando:</span><span class="sxs-lookup"><span data-stu-id="624c1-168">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```
  Install-Module -Name AzureAD 
  ```

<span data-ttu-id="624c1-169">Si se le pregunta si quiere instalar un módulo desde un repositorio que no es de confianza, escriba **Y** y presione ENTRAR.</span><span class="sxs-lookup"><span data-stu-id="624c1-169">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>


### <a name="step-2-connect-to-office-365"></a><span data-ttu-id="624c1-170">Paso 2: Conectarse a Office 365</span><span class="sxs-lookup"><span data-stu-id="624c1-170">Step 2: Connect to Office 365</span></span>

<span data-ttu-id="624c1-171">Para conectarse a su suscripción de Office 365 mediante el *nombre de cuenta y la contraseña*:</span><span class="sxs-lookup"><span data-stu-id="624c1-171">To connect to your Office 365 subscription with an *account name and password*:</span></span>
    
```
$UserCredential = Get-Credential
Connect-AzureAD -Credential $UserCredential
```

<span data-ttu-id="624c1-172">En el cuadro de diálogo **Solicitud de credenciales para Windows PowerShell**, escriba su nombre de usuario y contraseña de Office 365cuenta profesional o educativa y, luego, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="624c1-172">In the **Windows PowerShell Credential Request** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>
    
<span data-ttu-id="624c1-173">Para conectarse a su suscripción de Office 365 mediante la *autenticación multifactor (MFA)*:</span><span class="sxs-lookup"><span data-stu-id="624c1-173">To connect to your Office 365 subscription with *multi-factor authentication (MFA)*:</span></span>

```
Connect-AzureAD
```

<span data-ttu-id="624c1-174">En el cuadro de diálogo **Azure Active Directory PowerShell**, escriba su nombre de usuario y contraseña de Office 365cuenta profesional o educativa y, a continuación, haga clic en **Iniciar sesión**.</span><span class="sxs-lookup"><span data-stu-id="624c1-174">In the **Azure Active Directory PowerShell** dialog box, type your Office 365 work or school account user name and password, and then click **Sign in**.</span></span>
    
<span data-ttu-id="624c1-175">Siga las instrucciones del cuadro de diálogo de **Azure Active Directory PowerShell** para proporcionar información de autenticación adicional, como un código de comprobación, y haga clic en **Iniciar sesión**.</span><span class="sxs-lookup"><span data-stu-id="624c1-175">Follow the instructions in the **Azure Active Directory PowerShell** dialog box to provide additional authentication information, such as a verification code, and then click **Sign in**.</span></span>
    
<span data-ttu-id="624c1-176">Después de conectarse, podrá usar los nuevos cmdlets del [módulo de PowerShell Azure Active Directory V2](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span><span class="sxs-lookup"><span data-stu-id="624c1-176">After connecting, you can use the new cmdlets for the [Azure Active Directory V2 PowerShell module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="624c1-177">Consulte también</span><span class="sxs-lookup"><span data-stu-id="624c1-177">See also</span></span>

- [<span data-ttu-id="624c1-178">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="624c1-178">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="624c1-179">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="624c1-179">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="624c1-180">Conectarse a todos los servicios de Office 365 en una sola ventana de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="624c1-180">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [<span data-ttu-id="624c1-181">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="624c1-181">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [<span data-ttu-id="624c1-182">Connect-MsolService</span><span class="sxs-lookup"><span data-stu-id="624c1-182">Connect-MsolService</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532375)

