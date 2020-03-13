---
title: Conectarse a PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/13/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: 'Resumen: conéctese a su organización de Office 365 con PowerShell de Office 365 para realizar tareas del Centro de administración desde la línea de comandos.'
ms.openlocfilehash: 96ad47e6f60d6e098deffb48c56b4004d732b033
ms.sourcegitcommit: 48d8d40f546d452a0068260571d8d147e1c9de22
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "42616961"
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="fe25a-103">Conectarse a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="fe25a-103">Connect to Office 365 PowerShell</span></span>

<span data-ttu-id="fe25a-104">PowerShell de Office 365 le permite administrar la configuración de Office 365 desde la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="fe25a-104">Office 365 PowerShell lets you manage your Office 365 settings from the command line.</span></span> <span data-ttu-id="fe25a-105">Conectarse a PowerShell de Office 365 es un proceso sencillo que consiste en instalar el software necesario y conectarse a su organización de Office 365.</span><span class="sxs-lookup"><span data-stu-id="fe25a-105">Connecting to Office 365 PowerShell is a simple process where you install the required software and then connect to your Office 365 organization.</span></span> 

<span data-ttu-id="fe25a-106">Hay dos versiones del módulo de PowerShell que puede usar para conectarse a Office 365 y administrar cuentas de usuario, grupos y licencias:</span><span class="sxs-lookup"><span data-stu-id="fe25a-106">There are two versions of the PowerShell module that you use to connect to Office 365 and administer user accounts, groups, and licenses:</span></span>

- <span data-ttu-id="fe25a-107">Azure Active Directory PowerShell para Graph (los cmdlets incluyen **AzureAD** en su nombre)</span><span class="sxs-lookup"><span data-stu-id="fe25a-107">Azure Active Directory PowerShell for Graph (cmdlets include **AzureAD** in their name)</span></span>
- <span data-ttu-id="fe25a-108">Módulo Microsoft Azure Active Directory para Windows PowerShell (los cmdlets incluyen **MSol** en su nombre)</span><span class="sxs-lookup"><span data-stu-id="fe25a-108">Microsoft Azure Active Directory Module for Windows PowerShell (cmdlets include **MSol** in their name)</span></span> 

<span data-ttu-id="fe25a-109">En la fecha de este artículo, el Módulo MAzure Active Directory para Graph no reemplaza completamente la funcionalidad de los cmdlets del Módulo Microsoft Azure Active Directory para Windows PowerShell para la administración de usuarios, grupos y licencias.</span><span class="sxs-lookup"><span data-stu-id="fe25a-109">As of the date of this article, the Azure Active Directory PowerShell for Graph module does not completely replace the functionality in the cmdlets of Microsoft Azure Active Directory Module for Windows PowerShell module for user, group, and license administration.</span></span> <span data-ttu-id="fe25a-110">En muchos casos, deberá usar ambas versiones.</span><span class="sxs-lookup"><span data-stu-id="fe25a-110">In many cases, you need to use both versions.</span></span> <span data-ttu-id="fe25a-111">Puede instalar ambas versiones de forma segura en el mismo equipo.</span><span class="sxs-lookup"><span data-stu-id="fe25a-111">You can safely install both versions on the same computer.</span></span>

## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="fe25a-112">¿Qué necesita saber antes de empezar?</span><span class="sxs-lookup"><span data-stu-id="fe25a-112">What do you need to know before you begin?</span></span>

<span data-ttu-id="fe25a-113">Puede usar las siguientes versiones de Windows:</span><span class="sxs-lookup"><span data-stu-id="fe25a-113">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="fe25a-114">Windows 10, Windows 8.1, Windows 8 o Windows 7 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="fe25a-114">Windows 10, Windows 8.1, Windows 8, or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="fe25a-115">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 o Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="fe25a-115">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>

    > [!NOTE]
    > <span data-ttu-id="fe25a-116">Debe usar la versión 5.1 o posterior de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fe25a-116">You must use PowerShell version 5.1 or later.</span></span> <span data-ttu-id="fe25a-117">Para Windows 8.1, Windows 8, Windows 7 Service Pack 1 (SP1), Windows Server 2012 R2, Windows Server 2012 y Windows Server 2008 R2 SP1, descargue e instale [Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616).</span><span class="sxs-lookup"><span data-stu-id="fe25a-117">For Windows 8.1, Windows 8, Windows 7 Service Pack 1 (SP1), Windows Server 2012 R2, Windows Server 2012, and Windows Server 2008 R2 SP1, download and install the [Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616).</span></span> 
    
    > [!NOTE]
    ><span data-ttu-id="fe25a-p104">Use una versión de 64 bits de Windows. La compatibilidad con la versión de 32 bits de Módulo de Microsoft Azure Active Directory para Windows PowerShell se descontinuó en octubre de 2014.</span><span class="sxs-lookup"><span data-stu-id="fe25a-p104">Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
<span data-ttu-id="fe25a-120">Estos procedimientos están diseñados para los usuarios que sean miembros de un rol de administrador de Office 365.</span><span class="sxs-lookup"><span data-stu-id="fe25a-120">These procedures are intended for users who are members of an Office 365 admin role.</span></span> <span data-ttu-id="fe25a-121">Para obtener más información, vea [Información sobre los roles de administrador de Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="fe25a-121">For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="fe25a-122">Conéctese al módulo de PowerShell de Azure Active Directory para Graph</span><span class="sxs-lookup"><span data-stu-id="fe25a-122">Connect with the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="fe25a-123">Los comandos del módulo de [PowerShell Azure Active Directory para Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) incluyen **AzureAD** en su nombre de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fe25a-123">Commands in the [Azure Active Directory PowerShell for Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) module have **AzureAD** in their cmdlet name.</span></span>

<span data-ttu-id="fe25a-124">Para los procedimientos que necesitan los nuevos cmdlets del módulo de PowerShell Azure Active Directory para Graph, siga estos pasos para instalar el módulo y conectarse a su suscripción a Office 365.</span><span class="sxs-lookup"><span data-stu-id="fe25a-124">For procedures that require the new cmdlets in the Azure Active Directory PowerShell for Graph module, use these steps to install the module and connect to your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="fe25a-125">Vea [Módulo de PowerShell Azure Active Directory para Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) para obtener información sobre la compatibilidad con diferentes versiones de Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="fe25a-125">See [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) for information about the support for different versions of Microsoft Windows.</span></span>
>

### <a name="step-1-install-required-software"></a><span data-ttu-id="fe25a-126">Paso 1: Instalar el software necesario</span><span class="sxs-lookup"><span data-stu-id="fe25a-126">Step 1: Install required software</span></span>

<span data-ttu-id="fe25a-p106">Estos pasos son necesarios una sola vez en el equipo, no cada vez que se conecta. Sin embargo, probablemente necesitará instalar las versiones más recientes de software periódicamente.</span><span class="sxs-lookup"><span data-stu-id="fe25a-p106">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1. <span data-ttu-id="fe25a-129">Abra un símbolo del sistema de Windows PowerShell con privilegios elevados (ejecute Windows PowerShell como administrador).</span><span class="sxs-lookup"><span data-stu-id="fe25a-129">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="fe25a-130">En la ventana de comandos **Administrador: Windows PowerShell**, ejecute este comando:</span><span class="sxs-lookup"><span data-stu-id="fe25a-130">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```powershell
  Install-Module -Name AzureAD
  ```

<span data-ttu-id="fe25a-131">Si se le pregunta si quiere instalar un módulo desde un repositorio que no es de confianza, escriba **Y** y presione ENTRAR.</span><span class="sxs-lookup"><span data-stu-id="fe25a-131">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="fe25a-132">Paso 2: Conectarse a Azure AD para la suscripción de Office 365</span><span class="sxs-lookup"><span data-stu-id="fe25a-132">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="fe25a-133">Para conectarse a Azure AD para la suscripción de Office 365 con un nombre de cuenta y contraseña o con la autenticación multifactor (MFA), ejecute uno de estos comandos desde un símbolo del sistema de Windows PowerShell (no tiene que ser elevado).</span><span class="sxs-lookup"><span data-stu-id="fe25a-133">To connect to Azure AD for your Office 365 subscription with an account name and password or with multi-factor authentication (MFA), run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="fe25a-134">**Nube de Office 365**</span><span class="sxs-lookup"><span data-stu-id="fe25a-134">**Office 365 cloud**</span></span> | <span data-ttu-id="fe25a-135">**Command**</span><span class="sxs-lookup"><span data-stu-id="fe25a-135">**Command**</span></span> |
| <span data-ttu-id="fe25a-136">Office 365 Worldwide (+GCC)</span><span class="sxs-lookup"><span data-stu-id="fe25a-136">Office 365 Worldwide (+GCC)</span></span> | `Connect-AzureAD` |
| <span data-ttu-id="fe25a-137">Office 365 ofrecido por 21Vianet</span><span class="sxs-lookup"><span data-stu-id="fe25a-137">Office 365 operated by 21 Vianet</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| <span data-ttu-id="fe25a-138">Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="fe25a-138">Office 365 Germany</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| <span data-ttu-id="fe25a-139">Office 365 U.S. Government DoD y Office 365 U.S. Government GCC High</span><span class="sxs-lookup"><span data-stu-id="fe25a-139">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

<span data-ttu-id="fe25a-140">En el cuadro de diálogo **Inicie sesión**, escriba su nombre de usuario y contraseña de la cuenta profesional o educativa de Office 365 y haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="fe25a-140">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="fe25a-141">Si usa MFA, siga las instrucciones en los cuadros de diálogo adicionales para proporcionar más información de autenticación, como un código de comprobación.</span><span class="sxs-lookup"><span data-stu-id="fe25a-141">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

<span data-ttu-id="fe25a-142">Después de conectar, puede usar los cmdlets para el módulo [PowerShell de Azure Active Directory para](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span><span class="sxs-lookup"><span data-stu-id="fe25a-142">After connecting, you can use the cmdlets for the [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="fe25a-143">Conectar con el Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fe25a-143">Connect with the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="fe25a-144">Los comandos del Módulo Microsoft Azure Active Directory para Windows PowerShell tienen **Msol** en el nombre de su cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fe25a-144">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>

>[!Note]
><span data-ttu-id="fe25a-145">PowerShell Core no es compatible con el Módulo Microsoft Azure Active Directory para Windows PowerShell ni los cmdlet que llevan **Msol** en su nombre.</span><span class="sxs-lookup"><span data-stu-id="fe25a-145">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="fe25a-146">Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fe25a-146">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="fe25a-147">Paso 1: Instalar el software necesario</span><span class="sxs-lookup"><span data-stu-id="fe25a-147">Step 1: Install required software</span></span>

<span data-ttu-id="fe25a-p108">Estos pasos son necesarios una sola vez en el equipo, no cada vez que se conecta. Sin embargo, probablemente necesitará instalar las versiones más recientes de software periódicamente.</span><span class="sxs-lookup"><span data-stu-id="fe25a-p108">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="fe25a-150">Instale la versión de 64 bits de Microsoft Online Services - Ayudante para el inicio de sesión: [Ayudante para el inicio de sesión de Microsoft Online Services para profesionales de TI (RTW)](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span><span class="sxs-lookup"><span data-stu-id="fe25a-150">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="fe25a-151">Instale el Módulo Microsoft Azure Active Directory para Windows PowerShell siguiendo estos pasos:</span><span class="sxs-lookup"><span data-stu-id="fe25a-151">Install the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="fe25a-152">Abra un símbolo del sistema de Windows PowerShell con privilegios elevados (ejecute Windows PowerShell como administrador).</span><span class="sxs-lookup"><span data-stu-id="fe25a-152">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
  - <span data-ttu-id="fe25a-153">Ejecute el comando **Install-Module MSOnline**.</span><span class="sxs-lookup"><span data-stu-id="fe25a-153">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="fe25a-154">Si se le pide que instale el proveedor de NuGet, escriba **Y** y presione ENTRAR.</span><span class="sxs-lookup"><span data-stu-id="fe25a-154">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="fe25a-155">Si se le pide que instale el módulo desde PSGallery, escriba **Y** y presione ENTRAR.</span><span class="sxs-lookup"><span data-stu-id="fe25a-155">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="fe25a-156">Paso 2: Conectarse a Azure AD para la suscripción de Office 365</span><span class="sxs-lookup"><span data-stu-id="fe25a-156">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="fe25a-157">Para conectarse a Azure AD para la suscripción de Office 365 con un nombre de cuenta y contraseña o con la autenticación multifactor (MFA), ejecute uno de estos comandos desde un símbolo del sistema de Windows PowerShell (no tiene que ser elevado).</span><span class="sxs-lookup"><span data-stu-id="fe25a-157">To connect to Azure AD for your Office 365 subscription with an account name and password or with multi-factor authentication (MFA), run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="fe25a-158">**Nube de Office 365**</span><span class="sxs-lookup"><span data-stu-id="fe25a-158">**Office 365 cloud**</span></span> | <span data-ttu-id="fe25a-159">**Command**</span><span class="sxs-lookup"><span data-stu-id="fe25a-159">**Command**</span></span> |
| <span data-ttu-id="fe25a-160">Office 365 Worldwide (+GCC)</span><span class="sxs-lookup"><span data-stu-id="fe25a-160">Office 365 Worldwide (+GCC)</span></span> | `Connect-MsolService` |
| <span data-ttu-id="fe25a-161">Office 365 ofrecido por 21Vianet</span><span class="sxs-lookup"><span data-stu-id="fe25a-161">Office 365 operated by 21 Vianet</span></span> | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| <span data-ttu-id="fe25a-162">Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="fe25a-162">Office 365 Germany</span></span> | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| <span data-ttu-id="fe25a-163">Office 365 U.S. Government DoD y Office 365 U.S. Government GCC High</span><span class="sxs-lookup"><span data-stu-id="fe25a-163">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

<span data-ttu-id="fe25a-164">En el cuadro de diálogo **Inicie sesión**, escriba su nombre de usuario y contraseña de la cuenta profesional o educativa de Office 365 y haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="fe25a-164">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="fe25a-165">Si usa MFA, siga las instrucciones en los cuadros de diálogo adicionales para proporcionar más información de autenticación, como un código de comprobación.</span><span class="sxs-lookup"><span data-stu-id="fe25a-165">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="fe25a-166">¿Cómo saber si el proceso se completó correctamente?</span><span class="sxs-lookup"><span data-stu-id="fe25a-166">How do you know this worked?</span></span>

<span data-ttu-id="fe25a-p109">Si no se muestra ningún error, la conexión se habrá establecido correctamente. Para hacer una prueba rápida, ejecute un cmdlet de Office 365, como **Get-MsolUser**, y vea los resultados.</span><span class="sxs-lookup"><span data-stu-id="fe25a-p109">If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="fe25a-169">Si surgen errores, compruebe los siguientes requisitos:</span><span class="sxs-lookup"><span data-stu-id="fe25a-169">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="fe25a-170">**Un problema habitual es una contraseña incorrecta**.</span><span class="sxs-lookup"><span data-stu-id="fe25a-170">**A common problem is an incorrect password**.</span></span> <span data-ttu-id="fe25a-171">Vuelva a realizar el paso 2.</span><span class="sxs-lookup"><span data-stu-id="fe25a-171">Run Step 2 again.</span></span> <span data-ttu-id="fe25a-172">y preste especial atención al nombre de usuario y la contraseña que escriba.</span><span class="sxs-lookup"><span data-stu-id="fe25a-172">and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="fe25a-p111">**El Módulo de Microsoft Azure Active Directory para Windows PowerShell requiere que la característica Microsoft .NET Framework 3.5.* x* esté habilitada en el equipo\*\*. Es probable que el equipo tenga instalada una versión más reciente (por ejemplo, 4 o 4.5. *x*), pero sea posible habilitar o deshabilitar la compatibilidad con versiones anteriores de .NET Framework. Para obtener más información al respecto, consulte los temas siguientes:</span><span class="sxs-lookup"><span data-stu-id="fe25a-p111">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5.* x* feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.* x*), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled. For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="fe25a-175">Para Windows Server 2012 o Windows Server 2012 R2, vea [Habilitar .NET Framework 3.5 con el Asistente para agregar roles y características](https://go.microsoft.com/fwlink/p/?LinkId=532368).</span><span class="sxs-lookup"><span data-stu-id="fe25a-175">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="fe25a-176">Para Windows 7 o Windows Server 2008 R2, vea [No puede abrir el Módulo de Azure Active Directory para Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370).</span><span class="sxs-lookup"><span data-stu-id="fe25a-176">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>

  - <span data-ttu-id="fe25a-177">Para Windows 10, Windows 8.1 y Windows 8, vea [Instalar .NET Framework 3.5 en Windows 10, Windows 8.1 y Windows 8](https://docs.microsoft.com/dotnet/framework/install/dotnet-35-windows-10)</span><span class="sxs-lookup"><span data-stu-id="fe25a-177">For Windows 10, Windows 8.1, and Windows 8, see [Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8](https://docs.microsoft.com/dotnet/framework/install/dotnet-35-windows-10)</span></span>

  
- <span data-ttu-id="fe25a-p112">**Puede que su versión de Módulo de Microsoft Azure Active Directory para Windows PowerShell esté obsoleta.** Para comprobarlo, ejecute el siguiente comando en PowerShell de Office 365 o Módulo de Microsoft Azure Active Directory para Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fe25a-p112">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```powershell
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="fe25a-180">Si el número de versión devuelto es menor que el valor 1.0.8070.2, desinstale el Módulo de Microsoft Azure Active Directory para Windows PowerShell e instale la versión más reciente desde el vínculo en el paso 1.</span><span class="sxs-lookup"><span data-stu-id="fe25a-180">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="fe25a-181">**Si recibe un error de conexión, vea este tema:** [Error “Connect-MsolService: Se produjo una excepción de tipo”](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span><span class="sxs-lookup"><span data-stu-id="fe25a-181">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="fe25a-182">Vea también</span><span class="sxs-lookup"><span data-stu-id="fe25a-182">See also</span></span>

- [<span data-ttu-id="fe25a-183">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="fe25a-183">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="fe25a-184">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="fe25a-184">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="fe25a-185">Conectarse a todos los servicios de Office 365 en una sola ventana de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fe25a-185">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
