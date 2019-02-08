---
title: Conectarse a PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: 'Resumen: Conéctese a la organización de Office 365 con Office 365 PowerShell para realizar tareas de centro de administración de la línea de comandos.'
ms.openlocfilehash: ae0449611703759105d92a706cf78ba4a58ad4b2
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897203"
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="eb69d-103">Conectarse a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="eb69d-103">Connect to Office 365 PowerShell</span></span>

 <span data-ttu-id="eb69d-104">**Resumen:** Conectarse a la organización de Office 365 con Office 365 PowerShell para realizar tareas de administración desde la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="eb69d-104">**Summary:** Connect to your Office 365 organization using Office 365 PowerShell to perform administration tasks from the command line.</span></span>
  
<span data-ttu-id="eb69d-p101">PowerShell de Office 365 le permite administrar la configuración de Office 365 desde la línea de comandos. Conectarse a Office 365 PowerShell es un proceso simple que instalar el software requerido y, a continuación, conectarse a la organización de Office 365.</span><span class="sxs-lookup"><span data-stu-id="eb69d-p101">Office 365 PowerShell lets you manage your Office 365 settings from the command line. Connecting to Office 365 PowerShell is a simple process where you install the required software and then connect to your Office 365 organization.</span></span> 

<span data-ttu-id="eb69d-107">Hay dos versiones del módulo de PowerShell que use para conectarse a Office 365 y administrar las licencias, grupos y cuentas de usuario:</span><span class="sxs-lookup"><span data-stu-id="eb69d-107">There are two versions of the PowerShell module that you use to connect to Office 365 and administer user accounts, groups, and licenses:</span></span>

- <span data-ttu-id="eb69d-108">Azure Active Directory PowerShell para gráfico (cmdlets incluir **AzureAD** en su nombre)</span><span class="sxs-lookup"><span data-stu-id="eb69d-108">Azure Active Directory PowerShell for Graph (cmdlets include **AzureAD** in their name)</span></span> 
- <span data-ttu-id="eb69d-109">Microsoft Azure Active Directory módulo para Windows PowerShell (cmdlets incluir **MSol** en su nombre)</span><span class="sxs-lookup"><span data-stu-id="eb69d-109">Microsoft Azure Active Directory Module for Windows PowerShell (cmdlets include **MSol** in their name)</span></span> 

<span data-ttu-id="eb69d-p102">A partir de la fecha de este artículo, Azure Active Directory PowerShell para el módulo de gráfico no reemplazar completamente la funcionalidad en los cmdlets del módulo de Microsoft Azure Active Directory módulo para Windows PowerShell para el usuario, grupo y administración de licencias . En muchos casos, debe utilizar las dos versiones. Forma segura puede instalar ambas versiones en el mismo equipo.</span><span class="sxs-lookup"><span data-stu-id="eb69d-p102">As of the date of this article, the Azure Active Directory PowerShell for Graph module does not completely replace the functionality in the cmdlets of Microsoft Azure Active Directory Module for Windows PowerShell module for user, group, and license administration. In many cases, you need to use both versions. You can safely install both versions on the same computer.</span></span>

> [!TIP]
> <span data-ttu-id="eb69d-p103">**¿Es la primera vez que usa PowerShell?** Vea el [vídeo de información general sobre PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx) ofrecido por LinkedIn Learning.</span><span class="sxs-lookup"><span data-stu-id="eb69d-p103">**New to PowerShell?** See a [video Overview of PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), brought to you by LinkedIn Learning.</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="eb69d-115">¿Qué necesita saber antes de comenzar?</span><span class="sxs-lookup"><span data-stu-id="eb69d-115">What do you need to know before you begin?</span></span>

- <span data-ttu-id="eb69d-116">Tiempo estimado para finalizar: 5 minutos</span><span class="sxs-lookup"><span data-stu-id="eb69d-116">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="eb69d-117">Puede usar las siguientes versiones de Windows:</span><span class="sxs-lookup"><span data-stu-id="eb69d-117">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="eb69d-118">10 de Windows, Windows 8.1, Windows 8 o Windows 7 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="eb69d-118">Windows 10, Windows 8.1, Windows 8, or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="eb69d-119">Windows Server 2019, 2016 de Windows Server, Windows Server 2012 R2, Windows Server 2012 o Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="eb69d-119">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>
    
    > [!NOTE]
    ><span data-ttu-id="eb69d-p104">Use una versión de 64 bits de Windows. La compatibilidad con la versión de 32 bits de Módulo de Microsoft Azure Active Directory para Windows PowerShell se descontinuó en octubre de 2014.</span><span class="sxs-lookup"><span data-stu-id="eb69d-p104">Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
-  <span data-ttu-id="eb69d-p105">Estos procedimientos están diseñados para los usuarios que son miembros de un rol de administración de Office 365. Para obtener más información, vea [roles de administrador acerca de Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="eb69d-p105">These procedures are intended for users who are members of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="eb69d-124">Conectar con Azure Active Directory PowerShell para el módulo de gráfico</span><span class="sxs-lookup"><span data-stu-id="eb69d-124">Connect with the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="eb69d-125">Comandos en el módulo [Azure Active Directory PowerShell para gráfico](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) tienen **AzureAD** en su nombre de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eb69d-125">Commands in the [Azure Active Directory PowerShell for Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) module have **AzureAD** in their cmdlet name.</span></span>

<span data-ttu-id="eb69d-126">Para conocer los procedimientos que requieren los nuevos cmdlets en Azure Active Directory PowerShell para el módulo de gráfico, siga estos pasos para instalar el módulo y conectarlo a su suscripción de Office 365.</span><span class="sxs-lookup"><span data-stu-id="eb69d-126">For procedures that require the new cmdlets in the Azure Active Directory PowerShell for Graph module, use these steps to install the module and connect to your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="eb69d-127">Para obtener información acerca de la compatibilidad con diferentes versiones de Microsoft Windows, vea [Windows Azure Active Directory PowerShell para el módulo de gráfico](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) .</span><span class="sxs-lookup"><span data-stu-id="eb69d-127">See [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) for information about the support for different versions of Microsoft Windows.</span></span>
>

### <a name="step-1-install-required-software"></a><span data-ttu-id="eb69d-128">Paso 1: Instalar el software necesario</span><span class="sxs-lookup"><span data-stu-id="eb69d-128">Step 1: Install required software</span></span>

<span data-ttu-id="eb69d-p106">Estos pasos son necesarios una sola vez en el equipo, no cada vez que se conecta. Sin embargo, probablemente necesitará instalar las versiones más recientes de software periódicamente.</span><span class="sxs-lookup"><span data-stu-id="eb69d-p106">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1. <span data-ttu-id="eb69d-131">Abra un símbolo del sistema de Windows PowerShell con privilegios elevados (ejecute Windows PowerShell como administrador).</span><span class="sxs-lookup"><span data-stu-id="eb69d-131">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="eb69d-132">En la ventana de comandos **Administrador: Windows PowerShell**, ejecute este comando:</span><span class="sxs-lookup"><span data-stu-id="eb69d-132">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```
  Install-Module -Name AzureAD
  ```

<span data-ttu-id="eb69d-133">Si se le pregunta si quiere instalar un módulo desde un repositorio que no es de confianza, escriba **Y** y presione ENTRAR.</span><span class="sxs-lookup"><span data-stu-id="eb69d-133">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="eb69d-134">Paso 2: Conectarse a Azure AD para su suscripción de Office 365</span><span class="sxs-lookup"><span data-stu-id="eb69d-134">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="eb69d-135">Para conectarse a Azure AD para su suscripción de Office 365 con un nombre de cuenta y una contraseña o con *autenticación multifactor (MFA)*, ejecute uno de estos comandos desde un símbolo del sistema de Windows PowerShell (no tiene que ser con privilegios elevados).</span><span class="sxs-lookup"><span data-stu-id="eb69d-135">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)*, run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="eb69d-136">**Nube de Office 365**</span><span class="sxs-lookup"><span data-stu-id="eb69d-136">**Office 365 cloud**</span></span> | <span data-ttu-id="eb69d-137">**Comando**</span><span class="sxs-lookup"><span data-stu-id="eb69d-137">**Command**</span></span> |
| <span data-ttu-id="eb69d-138">Office 365 en todo el mundo (+ GCC)</span><span class="sxs-lookup"><span data-stu-id="eb69d-138">Office 365 Worldwide (+GCC)</span></span> | `Connect-AzureAD` |
| <span data-ttu-id="eb69d-139">Office 365 operado por Vianet 21</span><span class="sxs-lookup"><span data-stu-id="eb69d-139">Office 365 operated by 21 Vianet</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| <span data-ttu-id="eb69d-140">Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="eb69d-140">Office 365 Germany</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| <span data-ttu-id="eb69d-141">DoD de gobierno de Estados Unidos de Office 365 y gobierno de Estados Unidos de Office 365 GCC alta</span><span class="sxs-lookup"><span data-stu-id="eb69d-141">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

<span data-ttu-id="eb69d-142">En el cuadro de diálogo **Inicio de sesión en su cuenta** , escriba su trabajo de Office 365 o nombre de usuario de escuela cuenta y contraseña y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="eb69d-142">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="eb69d-143">Si está utilizando MFA, siga las instrucciones que aparecen en los cuadros de diálogo adicionales para proporcionar más información de autenticación, como un código de comprobación.</span><span class="sxs-lookup"><span data-stu-id="eb69d-143">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>


<span data-ttu-id="eb69d-144">Después de conectar, puede usar los cmdlets de nuevo para el [Azure Active Directory PowerShell para el módulo de gráfico](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span><span class="sxs-lookup"><span data-stu-id="eb69d-144">After connecting, you can use the new cmdlets for the [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="eb69d-145">Conectar con el Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="eb69d-145">Connect with the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="eb69d-146">Los comandos del Módulo Microsoft Azure Active Directory para Windows PowerShell tienen **Msol** en el nombre de su cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eb69d-146">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="eb69d-147">Paso 1: Instalar el software necesario</span><span class="sxs-lookup"><span data-stu-id="eb69d-147">Step 1: Install required software</span></span>

<span data-ttu-id="eb69d-p107">Estos pasos son necesarios una sola vez en el equipo, no cada vez que se conecta. Sin embargo, probablemente necesitará instalar las versiones más recientes de software periódicamente.</span><span class="sxs-lookup"><span data-stu-id="eb69d-p107">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="eb69d-150">Instale la versión de 64 bits de Microsoft Online Services - Ayudante para el inicio de sesión: [Ayudante para el inicio de sesión de Microsoft Online Services para profesionales de TI (RTW)](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span><span class="sxs-lookup"><span data-stu-id="eb69d-150">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="eb69d-151">Instale el Módulo Microsoft Azure Active Directory para Windows PowerShell siguiendo estos pasos:</span><span class="sxs-lookup"><span data-stu-id="eb69d-151">Install the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="eb69d-152">Abra un símbolo del sistema de Windows PowerShell con privilegios elevados (ejecute Windows PowerShell como administrador).</span><span class="sxs-lookup"><span data-stu-id="eb69d-152">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
  - <span data-ttu-id="eb69d-153">Ejecute el comando **Install-Module MSOnline**.</span><span class="sxs-lookup"><span data-stu-id="eb69d-153">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="eb69d-154">Si se le pide que instale el proveedor de NuGet, escriba **Y** y presione ENTRAR.</span><span class="sxs-lookup"><span data-stu-id="eb69d-154">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="eb69d-155">Si se le pide que instale el módulo desde PSGallery, escriba **Y** y presione ENTRAR.</span><span class="sxs-lookup"><span data-stu-id="eb69d-155">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="eb69d-156">Paso 2: Conectarse a Azure AD para su suscripción de Office 365</span><span class="sxs-lookup"><span data-stu-id="eb69d-156">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="eb69d-157">Para conectarse a Azure AD para su suscripción de Office 365 con un nombre de cuenta y una contraseña o con *autenticación multifactor (MFA)*, ejecute uno de estos comandos desde un símbolo del sistema de Windows PowerShell (no tiene que ser con privilegios elevados).</span><span class="sxs-lookup"><span data-stu-id="eb69d-157">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)*, run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="eb69d-158">**Nube de Office 365**</span><span class="sxs-lookup"><span data-stu-id="eb69d-158">**Office 365 cloud**</span></span> | <span data-ttu-id="eb69d-159">**Comando**</span><span class="sxs-lookup"><span data-stu-id="eb69d-159">**Command**</span></span> |
| <span data-ttu-id="eb69d-160">Office 365 en todo el mundo (+ GCC)</span><span class="sxs-lookup"><span data-stu-id="eb69d-160">Office 365 Worldwide (+GCC)</span></span> | `Connect-MsolService` |
| <span data-ttu-id="eb69d-161">Office 365 operado por Vianet 21</span><span class="sxs-lookup"><span data-stu-id="eb69d-161">Office 365 operated by 21 Vianet</span></span> | `Connect-MsolService -AzureEnvironmentName AzureChinaCloud` |
| <span data-ttu-id="eb69d-162">Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="eb69d-162">Office 365 Germany</span></span> | `Connect-MsolService -AzureEnvironmentName AzureGermanyCloud` |
| <span data-ttu-id="eb69d-163">DoD de gobierno de Estados Unidos de Office 365 y gobierno de Estados Unidos de Office 365 GCC alta</span><span class="sxs-lookup"><span data-stu-id="eb69d-163">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-MsolService -AzureEnvironmentName USGovernment` |
|||

<span data-ttu-id="eb69d-164">En el cuadro de diálogo **Inicio de sesión en su cuenta** , escriba su trabajo de Office 365 o nombre de usuario de escuela cuenta y contraseña y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="eb69d-164">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="eb69d-165">Si está utilizando MFA, siga las instrucciones que aparecen en los cuadros de diálogo adicionales para proporcionar más información de autenticación, como un código de comprobación.</span><span class="sxs-lookup"><span data-stu-id="eb69d-165">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="eb69d-166">¿Cómo saber si el proceso se ha completado correctamente?</span><span class="sxs-lookup"><span data-stu-id="eb69d-166">How do you know this worked?</span></span>

<span data-ttu-id="eb69d-p108">Si no se muestra ningún error, la conexión se habrá establecido correctamente. Para hacer una prueba rápida, ejecute un cmdlet de Office 365, como **Get-MsolUser**, y vea los resultados.</span><span class="sxs-lookup"><span data-stu-id="eb69d-p108">If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="eb69d-169">Si surgen errores, compruebe los siguientes requisitos:</span><span class="sxs-lookup"><span data-stu-id="eb69d-169">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="eb69d-p109">**Un problema común es una contraseña incorrecta**. Vuelva a ejecutar el paso 2. y preste especial atención para el nombre de usuario y la contraseña que especifique.</span><span class="sxs-lookup"><span data-stu-id="eb69d-p109">**A common problem is an incorrect password**. Run Step 2 again. and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="eb69d-p110">**El Módulo de Microsoft Azure Active Directory para Windows PowerShell requiere que la característica Microsoft .NET Framework 3.5.* x* esté habilitada en el equipo\*\*. Es probable que el equipo tenga instalada una versión más reciente (por ejemplo, 4 o 4.5. *x*), pero sea posible habilitar o deshabilitar la compatibilidad con versiones anteriores de .NET Framework. Para obtener más información al respecto, consulte los temas siguientes:</span><span class="sxs-lookup"><span data-stu-id="eb69d-p110">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5.* x* feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.* x*), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled. For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="eb69d-175">Para Windows Server 2012 o Windows Server 2012 R2, vea [Habilitar .NET Framework 3.5 con el Asistente para agregar roles y características](https://go.microsoft.com/fwlink/p/?LinkId=532368).</span><span class="sxs-lookup"><span data-stu-id="eb69d-175">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="eb69d-176">Para Windows 7 o Windows Server 2008 R2, vea [No puede abrir el Módulo de Azure Active Directory para Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370).</span><span class="sxs-lookup"><span data-stu-id="eb69d-176">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>

  - <span data-ttu-id="eb69d-177">Para Windows 10, Windows 8.1 y Windows 8, vea [instalar .NET Framework 3.5 en 10 de Windows, Windows 8.1 y Windows 8](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)</span><span class="sxs-lookup"><span data-stu-id="eb69d-177">For Windows 10, Windows 8.1, and Windows 8, see [Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)</span></span>

  
- <span data-ttu-id="eb69d-p111">**Puede que su versión de Módulo de Microsoft Azure Active Directory para Windows PowerShell esté obsoleta.** Para comprobarlo, ejecute el siguiente comando en PowerShell de Office 365 o Módulo de Microsoft Azure Active Directory para Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="eb69d-p111">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="eb69d-180">Si el número de versión devuelto es menor que el valor 1.0.8070.2, desinstale el Módulo de Microsoft Azure Active Directory para Windows PowerShell e instale la versión más reciente desde el vínculo en el paso 1.</span><span class="sxs-lookup"><span data-stu-id="eb69d-180">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="eb69d-181">**Si recibe un error de conexión, vea este tema:** [Error “Connect-MsolService: Se produjo una excepción de tipo”](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span><span class="sxs-lookup"><span data-stu-id="eb69d-181">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="eb69d-182">Consulte también</span><span class="sxs-lookup"><span data-stu-id="eb69d-182">See also</span></span>

- [<span data-ttu-id="eb69d-183">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="eb69d-183">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="eb69d-184">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="eb69d-184">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="eb69d-185">Conectarse a todos los servicios de Office 365 en una sola ventana de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="eb69d-185">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [<span data-ttu-id="eb69d-186">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="eb69d-186">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [<span data-ttu-id="eb69d-187">Connect-MsolService</span><span class="sxs-lookup"><span data-stu-id="eb69d-187">Connect-MsolService</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532375)

