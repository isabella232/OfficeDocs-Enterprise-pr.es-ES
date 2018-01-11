---
title: "Sincronización de directorios (DirSync) para el entorno de desarrollo y pruebas de Office 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Strat_O365_Enterprise
- TLG
- Ent_TLGs
ms.assetid: e6b27e25-74ae-4b54-9421-c8e911aef543
description: "Resumen: Configurar la sincronización de directorios para el entorno de desarrollo y prueba de Office 365."
ms.openlocfilehash: d8a663367e61ac3f01e67f4d3731a0dccdd5a222
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2018
---
# <a name="dirsync-for-your-office-365-devtest-environment"></a><span data-ttu-id="52c5a-103">Sincronización de directorios (DirSync) para el entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="52c5a-103">DirSync for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="52c5a-104">**Resumen:** Configurar la sincronización de directorios para el entorno de desarrollo y prueba de Office 365.</span><span class="sxs-lookup"><span data-stu-id="52c5a-104">**Summary:** Configure directory synchronization for your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="52c5a-p101">Muchas organizaciones usan Azure Connect de AD y la sincronización de directorios (DirSync) para sincronizar el conjunto de cuentas de su bosque de Windows Server Active Directory (AD) local para el conjunto de cuentas de Office 365. En este artículo se describe cómo puede agregar DirSync con sincronización de contraseñas al entorno de desarrollo y pruebas de Office 365, dando como resultado la siguiente configuración.</span><span class="sxs-lookup"><span data-stu-id="52c5a-p101">Many organizations use Azure AD Connect and directory synchronization (DirSync) to synchronize the set of accounts in their on-premises Windows Server Active Directory (AD) forest to the set of accounts in Office 365. This article describes how you can add DirSync with password synchronization to the Office 365 dev/test environment, resulting in the following configuration.</span></span>
  
![El entorno de desarrollo y prueba de Office 365 con DirSync](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="52c5a-108">Esta configuración se compone de: </span><span class="sxs-lookup"><span data-stu-id="52c5a-108">This configuration consists of:</span></span> 
  
- <span data-ttu-id="52c5a-109">Una suscripción de prueba a Office 365 E5, que expira a los 30 días de su creación.</span><span class="sxs-lookup"><span data-stu-id="52c5a-109">An Office 365 E5 Trial Subscription, which expires 30 days from when you create it.</span></span>
    
- <span data-ttu-id="52c5a-p102">La intranet de una organización simplificada conectada a Internet, que consta de tres máquinas virtuales en una subred de una red virtual de Azure (DC1, APP1 y CLIENTE1). Azure Connect de AD se ejecuta en APP1 para sincronizar el dominio de Windows Server AD con Office 365.</span><span class="sxs-lookup"><span data-stu-id="52c5a-p102">A simplified organization intranet connected to the Internet, consisting of three virtual machines on a subnet of an Azure virtual network (DC1, APP1, and CLIENT1). Azure AD Connect runs on APP1 to synchronize the Windows Server AD domain to Office 365.</span></span>
    
<span data-ttu-id="52c5a-112">Existen dos fases para configurar el entorno de desarrollo y pruebas:</span><span class="sxs-lookup"><span data-stu-id="52c5a-112">There are two phases to setting up this dev/test environment:</span></span>
  
1. <span data-ttu-id="52c5a-113">Crear el entorno de desarrollo y pruebas de Office 365 (las máquinas virtuales DC1, APP1 y CLIENTE1 en una red virtual Azure con una suscripción de prueba a Office 365 E5).</span><span class="sxs-lookup"><span data-stu-id="52c5a-113">Create the Office 365 dev/test environment (the DC1, APP1, and CLIENT1 virtual machines in an Azure virtual network with an Office 365 E5 trial subscription).</span></span>
    
2. <span data-ttu-id="52c5a-114">Instalar y configurar Azure AD Connect en APP1.</span><span class="sxs-lookup"><span data-stu-id="52c5a-114">Install and configure Azure AD Connect on APP1.</span></span>
    
> [!TIP]
> <span data-ttu-id="52c5a-115">Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual para todos los artículos de la pila de una guía de laboratorio de prueba de nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="52c5a-115">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-an-office-365-devtest-environment"></a><span data-ttu-id="52c5a-116">Fase 1: Crear un entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="52c5a-116">Phase 1: Create an Office 365 dev/test environment</span></span>

<span data-ttu-id="52c5a-p103">Siga las instrucciones en las fases 1, 2 y 3 del artículo del [entorno de desarrollo y prueba de Office 365](office-365-dev-test-environment.md) . Aquí está la configuración resultante.</span><span class="sxs-lookup"><span data-stu-id="52c5a-p103">Follow the instructions in phases 1, 2, and 3 of the [Office 365 dev/test environment](office-365-dev-test-environment.md) article. Here is the resulting configuration.</span></span>
  
![El entorno de desarrollo y prueba de Office 365](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
<span data-ttu-id="52c5a-120">Esta configuración se compone de: </span><span class="sxs-lookup"><span data-stu-id="52c5a-120">This configuration consists of:</span></span> 
  
- <span data-ttu-id="52c5a-121">Una suscripción de prueba a Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="52c5a-121">An Office 365 E5 Trial Subscription.</span></span>
    
- <span data-ttu-id="52c5a-122">La intranet de una organización simplificada conectada a Internet, que consta de las máquinas virtuales DC1, APP1 y CLIENTE1 en una subred de una red virtual de Azure.</span><span class="sxs-lookup"><span data-stu-id="52c5a-122">A simplified organization intranet connected to the Internet, consisting of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
    
## <a name="phase-2-install-azure-ad-connect-on-app1"></a><span data-ttu-id="52c5a-123">Fase 2: Instalar Azure AD Connect en APP1</span><span class="sxs-lookup"><span data-stu-id="52c5a-123">Phase 2: Install Azure AD Connect on APP1</span></span>

<span data-ttu-id="52c5a-p104">Una vez instalado y configurado, Azure Connect AD sincroniza el conjunto de cuentas del dominio CORP Windows Server AD con el conjunto de cuentas de su suscripción de prueba a Office 365. El siguiente procedimiento le guía a través de la instalación de Azure Connect AD en APP1 y la comprobación de que funciona.</span><span class="sxs-lookup"><span data-stu-id="52c5a-p104">Once installed and configured, Azure AD Connect synchronizes the set of accounts in the CORP Windows Server AD domain with the set of accounts in your Office 365 trial subscription. The following procedure steps you through installing Azure AD Connect on APP1 and verifying that it works.</span></span>
  
### <a name="install-and-configure-azure-ad-connect-on-app1"></a><span data-ttu-id="52c5a-126">Instalar y configurar Azure Connect de AD en APP1</span><span class="sxs-lookup"><span data-stu-id="52c5a-126">Install and configure Azure AD Connect on APP1</span></span>

1. <span data-ttu-id="52c5a-127">Desde el [portal de Azure](https://portal.azure.com), conéctese a APP1 con el CORP\\cuenta de Usuario1.</span><span class="sxs-lookup"><span data-stu-id="52c5a-127">From the [Azure portal](https://portal.azure.com), connect to APP1 with the CORP\\User1 account.</span></span>
    
2. <span data-ttu-id="52c5a-128">Desde APP1, abra un símbolo del sistema de Windows PowerShell con el nivel de administrador y ejecute estos comandos:</span><span class="sxs-lookup"><span data-stu-id="52c5a-128">From APP1, open an administrator-level Windows PowerShell command prompt, and then run these commands:</span></span>
    
  ```
  Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force

  ```

3. <span data-ttu-id="52c5a-129">Desde la barra de tareas, haga clic en **Internet Explorer** y vaya a [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span><span class="sxs-lookup"><span data-stu-id="52c5a-129">From the task bar, click **Internet Explorer** and go to [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span></span>
    
4. <span data-ttu-id="52c5a-130">En la página Microsoft Azure Active Directory Connect, haga clic en **Descargar**y, a continuación, haga clic en **Ejecutar**.</span><span class="sxs-lookup"><span data-stu-id="52c5a-130">On the Microsoft Azure Active Directory Connect page, click **Download**, and then click **Run**.</span></span>
    
5. <span data-ttu-id="52c5a-131">En la página **Bienvenido a Azure Connect de AD** , haga clic en **Acepto**y, a continuación, haga clic en **continuar**.</span><span class="sxs-lookup"><span data-stu-id="52c5a-131">On the **Welcome to Azure AD Connect** page, click **I agree**, and then click **Continue**.</span></span>
    
6. <span data-ttu-id="52c5a-132">En la página **Configuración de Express** , haga clic en **Usar configuración express**.</span><span class="sxs-lookup"><span data-stu-id="52c5a-132">On the **Express Settings** page, click **Use express settings**.</span></span>
    
7. <span data-ttu-id="52c5a-133">En la página **Conectar a Azure AD** , escriba su nombre de cuenta de administrador global en **nombre de usuario,** escriba su contraseña en **contraseña**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="52c5a-133">On the **Connect to Azure AD** page, type your global administrator account name in **Username,** type its password in **Password**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="52c5a-134">En la página **Conectar con AD DS** , escriba **CORP\\Usuario1** en **nombre de usuario,** escriba su contraseña en **contraseña**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="52c5a-134">On the **Connect to AD DS** page, type **CORP\\User1** in **Username,** type its password in **Password**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="52c5a-135">En la página de **configuración de inicio de sesión de anuncio de Azure** , haga clic en **continuar sin ningún verificados dominios**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="52c5a-135">On the **Azure AD sign-in configuration** page, click **Continue without any verified domains**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="52c5a-136">En la página **Listo para configurar**, haga clic en **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="52c5a-136">On the **Ready to configure** page, click **Install**.</span></span>
    
11. <span data-ttu-id="52c5a-137">En la página **Configuración finalizada** , haga clic en **Salir**.</span><span class="sxs-lookup"><span data-stu-id="52c5a-137">On the **Configuration complete** page, click **Exit**.</span></span>
    
12. <span data-ttu-id="52c5a-138">En Internet Explorer, vaya al portal de Office 365 ([https://portal.office.com](https://portal.office.com)) e iniciar sesión en su suscripción de prueba de Office 365 con su cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="52c5a-138">In Internet Explorer, go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
13. <span data-ttu-id="52c5a-139">Desde la página principal del portal, haga clic en **Admin**.</span><span class="sxs-lookup"><span data-stu-id="52c5a-139">From the main portal page, click **Admin**.</span></span>
    
14. <span data-ttu-id="52c5a-140">En el panel de navegación izquierdo, haga clic en **Usuarios > Usuarios activos**.</span><span class="sxs-lookup"><span data-stu-id="52c5a-140">In the left navigation, click **Users > Active users**.</span></span>
    
    <span data-ttu-id="52c5a-p105">Nota la cuenta denominada **Usuario1**. Esta cuenta es desde el dominio CORP Windows Server AD y es la prueba de que ha trabajado la sincronización de directorios.</span><span class="sxs-lookup"><span data-stu-id="52c5a-p105">Note the account named **User1**. This account is from the CORP Windows Server AD domain and is proof that DirSync has worked.</span></span>
    
15. <span data-ttu-id="52c5a-p106">Haga clic en la cuenta de **Usuario1** . Licencias de producto, haga clic en **Editar**.</span><span class="sxs-lookup"><span data-stu-id="52c5a-p106">Click the **User1** account. For product licenses, click **Edit**.</span></span>
    
16. <span data-ttu-id="52c5a-p107">En las **licencias de producto**, seleccione su país y haga clic en el control de **apagado** para **Office 365 Enterprise E5** (conmutación en **On**). Haga clic en **Guardar** en la parte inferior de la página y, a continuación, haga clic en **Cerrar**.</span><span class="sxs-lookup"><span data-stu-id="52c5a-p107">In **Product licenses**, select your country, and then click the **Off** control for **Office 365 Enterprise E5** (switching it to **On**). Click **Save** at the bottom of the page, and then click **Close**.</span></span>
    
<span data-ttu-id="52c5a-147">Esta es la configuración resultante.</span><span class="sxs-lookup"><span data-stu-id="52c5a-147">This is the resulting configuration.</span></span>
  
![El entorno de desarrollo y prueba de Office 365 con DirSync](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="52c5a-149">Esta configuración se compone de: </span><span class="sxs-lookup"><span data-stu-id="52c5a-149">This configuration consists of:</span></span> 
  
- <span data-ttu-id="52c5a-150">Una suscripción de prueba a Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="52c5a-150">An Office 365 E5 Trial Subscription.</span></span>
    
- <span data-ttu-id="52c5a-p108">La intranet de una organización simplificada conectada a Internet, que consta de las máquinas virtuales DC1, APP1 y CLIENTE1 en una subred de una red virtual de Azure. Azure Connect de AD se ejecuta en APP1 para sincronizar el dominio de Windows Server AD de CORP con Office 365 cada 30 minutos.</span><span class="sxs-lookup"><span data-stu-id="52c5a-p108">A simplified organization intranet connected to the Internet, consisting of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network. Azure AD Connect runs on APP1 to synchronize the CORP Windows Server AD domain to Office 365 every 30 minutes.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="52c5a-153">Paso siguiente</span><span class="sxs-lookup"><span data-stu-id="52c5a-153">Next Step</span></span>

<span data-ttu-id="52c5a-154">Cuando esté listo para implementar la sincronización de directorios para su organización, consulte [Implementar Office 365 sincronización de directorios (DirSync) de Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span><span class="sxs-lookup"><span data-stu-id="52c5a-154">When you are ready to deploy DirSync for your organization, see [Deploy Office 365 Directory Synchronization (DirSync) in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="52c5a-155">Consulte también</span><span class="sxs-lookup"><span data-stu-id="52c5a-155">See Also</span></span>

[<span data-ttu-id="52c5a-156">Guías del laboratorio de pruebas de adopción de la nube (TLG)</span><span class="sxs-lookup"><span data-stu-id="52c5a-156">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="52c5a-157">Entorno de desarrollo y pruebas de la configuración básica</span><span class="sxs-lookup"><span data-stu-id="52c5a-157">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="52c5a-158">Entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="52c5a-158">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="52c5a-159">Seguridad de la aplicación de nube para su entorno de pruebas y desarrollo de Office 365</span><span class="sxs-lookup"><span data-stu-id="52c5a-159">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="52c5a-160">Una protección avanzada para su entorno de pruebas y desarrollo de Office 365</span><span class="sxs-lookup"><span data-stu-id="52c5a-160">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="52c5a-161">Adopción de la nube y soluciones híbridas</span><span class="sxs-lookup"><span data-stu-id="52c5a-161">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




