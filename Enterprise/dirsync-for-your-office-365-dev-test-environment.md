---
title: Configurar la sincronización de directorios para el entorno de desarrollo y pruebas de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/04/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: e6b27e25-74ae-4b54-9421-c8e911aef543
description: 'Resumen: configure la sincronización de directorios para el entorno de desarrollo y pruebas de Office 365.'
ms.openlocfilehash: 209b41e4d695a753867d989b8f27b96618a81303
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2018
---
# <a name="directory-synchronization-for-your-office-365-devtest-environment"></a><span data-ttu-id="448e0-103">Configurar la sincronización de directorios para el entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="448e0-103">Summary: Configure directory synchronization for your Office 365 dev/test environment.</span></span>

 <span data-ttu-id="448e0-104">**Resumen:** configure la sincronización de directorios para el entorno de desarrollo y pruebas de Office 365.</span><span class="sxs-lookup"><span data-stu-id="448e0-104">**Summary:** Configure directory synchronization for your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="448e0-p101">Muchas organizaciones usan Azure AD Connect y la sincronización de directorios para sincronizar el conjunto de cuentas de su bosque de Windows Server Active Directory (AD) local para el conjunto de cuentas de Office 365. En este artículo, se describe cómo agregar la sincronización de directorios con la sincronización de hash de contraseña al entorno de desarrollo y pruebas de Office 365, lo que da como resultado la siguiente configuración.</span><span class="sxs-lookup"><span data-stu-id="448e0-p101">Many organizations use Azure AD Connect and directory synchronization (DirSync) to synchronize the set of accounts in their on-premises Windows Server Active Directory (AD) forest to the set of accounts in Office 365. This article describes how you can add DirSync with password synchronization to the Office 365 dev/test environment, resulting in the following configuration.</span></span>
  
![Entorno de desarrollo y pruebas de Office 365 con sincronización de directorios](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="448e0-108">Esta configuración se compone de:</span><span class="sxs-lookup"><span data-stu-id="448e0-108">This configuration consists of:</span></span> 
  
- <span data-ttu-id="448e0-109">Una suscripción de prueba a Office 365 E5, que expira a los 30 días de su creación.</span><span class="sxs-lookup"><span data-stu-id="448e0-109">An Office 365 E5 Trial Subscription, which expires 30 days from when you create it.</span></span>
- <span data-ttu-id="448e0-p102">La intranet de una organización simplificada conectada a Internet, que consta de tres máquinas virtuales en una subred de una red virtual de Azure (DC1, APP1 y CLIENTE1). Azure Connect de AD se ejecuta en APP1 para sincronizar el dominio de Windows Server AD con Office 365.</span><span class="sxs-lookup"><span data-stu-id="448e0-p102">A simplified organization intranet connected to the Internet, consisting of three virtual machines on a subnet of an Azure virtual network (DC1, APP1, and CLIENT1). Azure AD Connect runs on APP1 to synchronize the Windows Server AD domain to Office 365.</span></span>
    
<span data-ttu-id="448e0-112">Existen dos fases para configurar el entorno de desarrollo y pruebas:</span><span class="sxs-lookup"><span data-stu-id="448e0-112">There are two phases to setting up this dev/test environment:</span></span>
  
1. <span data-ttu-id="448e0-113">Crear el entorno de desarrollo y pruebas de Office 365 (las máquinas virtuales DC1, APP1 y CLIENTE1 en una red virtual Azure con una suscripción de prueba a Office 365 E5).</span><span class="sxs-lookup"><span data-stu-id="448e0-113">Create the Office 365 dev/test environment (the DC1, APP1, and CLIENT1 virtual machines in an Azure virtual network with an Office 365 E5 trial subscription).</span></span>
2. <span data-ttu-id="448e0-114">Instalar y configurar Azure AD Connect en APP1.</span><span class="sxs-lookup"><span data-stu-id="448e0-114">Install and configure Azure AD Connect on APP1.</span></span>
    
> [!TIP]
> <span data-ttu-id="448e0-115">Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual de todos los artículos en la pila de la Guía del entorno de pruebas de One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="448e0-115">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-an-office-365-devtest-environment"></a><span data-ttu-id="448e0-116">Fase 1: Crear un entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="448e0-116">Phase 1: Create an Office 365 dev/test environment</span></span>

<span data-ttu-id="448e0-p103">Siga las instrucciones de las fases 1, 2 y 3 del artículo [Entorno de desarrollo y pruebas de Office 365](office-365-dev-test-environment.md). Esta es la configuración resultante.</span><span class="sxs-lookup"><span data-stu-id="448e0-p103">Follow the instructions in phases 1, 2, and 3 of the Create an Office 365 Dev/Test Environment article. Here is the resulting configuration.</span></span>
  
![El entorno de desarrollo y pruebas de Office 365](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
<span data-ttu-id="448e0-120">Esta configuración se compone de:</span><span class="sxs-lookup"><span data-stu-id="448e0-120">This configuration consists of:</span></span> 
  
- <span data-ttu-id="448e0-121">Una suscripción de prueba a Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="448e0-121">An Office 365 E5 Trial Subscription.</span></span>
- <span data-ttu-id="448e0-122">La intranet de una organización simplificada conectada a Internet, que consta de las máquinas virtuales DC1, APP1 y CLIENTE1 en una subred de una red virtual de Azure.</span><span class="sxs-lookup"><span data-stu-id="448e0-122">A simplified organization intranet connected to the Internet, consisting of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
    
## <a name="phase-2-install-azure-ad-connect-on-app1"></a><span data-ttu-id="448e0-123">Fase 2: Instalar Azure AD Connect en APP1</span><span class="sxs-lookup"><span data-stu-id="448e0-123">Phase 2: Install Azure AD Connect on APP1</span></span>

<span data-ttu-id="448e0-p104">Una vez instalado y configurado, Azure Connect AD sincroniza el conjunto de cuentas del dominio CORP Windows Server AD con el conjunto de cuentas de su suscripción de prueba a Office 365. El siguiente procedimiento le guía a través de la instalación de Azure Connect AD en APP1 y la comprobación de que funciona.</span><span class="sxs-lookup"><span data-stu-id="448e0-p104">Once installed and configured, Azure AD Connect synchronizes the set of accounts in the CORP Windows Server AD domain with the set of accounts in your Office 365 trial subscription. The following procedure steps you through installing Azure AD Connect on APP1 and verifying that it works.</span></span>
  
### <a name="install-and-configure-azure-ad-connect-on-app1"></a><span data-ttu-id="448e0-126">Instalar y configurar Azure AD Connect en APP1</span><span class="sxs-lookup"><span data-stu-id="448e0-126">Install  and configure Azure AD Connect on APP1</span></span>

1. <span data-ttu-id="448e0-127">En [Azure Portal](https://portal.azure.com), conéctese a APP1 con la cuenta CORP\\Usuario1.</span><span class="sxs-lookup"><span data-stu-id="448e0-127">From the [Azure portalhttps://portal.azure.com](https://portal.azure.com), connect to APP1 with the CORP\User1 account.</span></span>
    
2. <span data-ttu-id="448e0-128">Desde APP1, abra un símbolo del sistema de Windows PowerShell con el nivel de administrador y ejecute estos comandos:</span><span class="sxs-lookup"><span data-stu-id="448e0-128">From APP1, open an administrator-level Windows PowerShell command prompt, and then run these commands:</span></span>
    
  ```
  Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force

  ```

3. <span data-ttu-id="448e0-129">En la barra de tareas, haga clic en **Internet Explorer** y vaya a [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span><span class="sxs-lookup"><span data-stu-id="448e0-129">From the task bar, click **Internet Explorer** and go to [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span></span>
    
4. <span data-ttu-id="448e0-130">En la página de Microsoft Azure Active Directory Connect, haga clic en **Descargar** y, después, en **Ejecutar**.</span><span class="sxs-lookup"><span data-stu-id="448e0-130">On the Microsoft Azure Active Directory Connect page, click **Download**, and then click **Run**.</span></span>
    
5. <span data-ttu-id="448e0-131">En la página **Bienvenido a Azure AD Connect**, haga clic en **Acepto** y, después, en **Continuar**.</span><span class="sxs-lookup"><span data-stu-id="448e0-131">On the **Welcome to Azure AD Connect** page, click **I agree**, and then click **Continue.**</span></span>
    
6. <span data-ttu-id="448e0-132">En la página **Configuración rápida**, haga clic en **Usar configuración rápida**.</span><span class="sxs-lookup"><span data-stu-id="448e0-132">On the **Express Settings** page, click  **Use express settings**.</span></span>
    
7. <span data-ttu-id="448e0-133">En la página **Conectar a Azure AD**, escriba el nombre de la cuenta de administrador global en **Nombre de usuario**, escriba la contraseña en **Contraseña** y, después, haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="448e0-133">On the **Connect to Azure AD** page, type your global administrator account name in **Username,** type its password in **Password**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="448e0-134">En la página **Conectarse a AD DS**, escriba **CORP\\Usuario1** en **Nombre de usuario**, escriba la contraseña en **Contraseña** y, después, haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="448e0-134">On the Connect to AD DS page, type CORP\User1 in Username, type its password in Password, and then click Next.</span></span>
    
9. <span data-ttu-id="448e0-135">En la página **Configuración de inicio de sesión de Azure AD**, haga clic en **Continuar sin dominios comprobados** y después en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="448e0-135">On the **Azure AD sign-in configuration** page, click **Continue without any verified domains**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="448e0-136">En la página **Listo para configurar**, haga clic en **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="448e0-136">On the **Ready to configure** page, click **Install**.</span></span>
    
11. <span data-ttu-id="448e0-137">En la página **Configuración completada** de página, haga clic en **Salir**.</span><span class="sxs-lookup"><span data-stu-id="448e0-137">On the **Configuration complete** page, click **Exit**.</span></span>
    
12. <span data-ttu-id="448e0-138">En Internet Explorer, vaya al portal de Office 365 ([https://portal.office.com](https://portal.office.com)) e inicie sesión en la suscripción de prueba de Office 365 con la cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="448e0-138">In Internet Explorer, go to the Office 365 portal ( https://portal.office.com https://portal.office.com ) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
13. <span data-ttu-id="448e0-139">En la página principal del portal, haga clic en **Administración**.</span><span class="sxs-lookup"><span data-stu-id="448e0-139">From the main portal page, click **Admin**.</span></span>
    
14. <span data-ttu-id="448e0-140">En el panel de navegación izquierdo, haga clic en **Usuarios > Usuarios activos**.</span><span class="sxs-lookup"><span data-stu-id="448e0-140">In the left navigation, click **Users > Active users**.</span></span>
    
    <span data-ttu-id="448e0-p105">Observe la cuenta llamada **Usuario1**. Esta cuenta pertenece al dominio CORP de Windows Server AD y es una prueba de que la sincronización de directorios funcionó correctamente.</span><span class="sxs-lookup"><span data-stu-id="448e0-p105">Note the account named **User1**. This account is from the CORP Windows Server AD domain and is proof that DirSync has worked.</span></span>
    
15. <span data-ttu-id="448e0-p106">Haga clic en la cuenta **Usuario1**. Para licencias de productos, haga clic en **Editar**.</span><span class="sxs-lookup"><span data-stu-id="448e0-p106">Click the **User1** account. For product licenses, click **Edit**.</span></span>
    
16. <span data-ttu-id="448e0-p107">En **Licencias de productos**, seleccione su país y, después, haga clic en el control **Desactivado** de **Office 365 Enterprise E5** (para cambiarlo a **Activado**). Haga clic en **Guardar** en la parte inferior de la página y, después, en **Cerrar**.</span><span class="sxs-lookup"><span data-stu-id="448e0-p107">In **Product licenses**, select your country, and then click the **Off** control for **Office 365 Enterprise E5** (switching it to **On**). Click **Save** at the bottom of the page, and then click **Close**.</span></span>
    
<span data-ttu-id="448e0-147">Esta es la configuración resultante.</span><span class="sxs-lookup"><span data-stu-id="448e0-147">This is the resulting configuration.</span></span>
  
![Entorno de desarrollo y pruebas de Office 365 con sincronización de directorios](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="448e0-149">Esta configuración se compone de:</span><span class="sxs-lookup"><span data-stu-id="448e0-149">This configuration consists of:</span></span> 
  
- <span data-ttu-id="448e0-150">Una suscripción de prueba a Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="448e0-150">An Office 365 E5 Trial Subscription.</span></span>
- <span data-ttu-id="448e0-p108">La intranet de una organización simplificada conectada a Internet, que consta de las máquinas virtuales DC1, APP1 y CLIENTE1 en una subred de una red virtual de Azure. Azure Connect de AD se ejecuta en APP1 para sincronizar el dominio de Windows Server AD de CORP con Office 365 cada 30 minutos.</span><span class="sxs-lookup"><span data-stu-id="448e0-p108">A simplified organization intranet connected to the Internet, consisting of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network. Azure AD Connect runs on APP1 to synchronize the CORP Windows Server AD domain to Office 365 every 30 minutes.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="448e0-153">Paso siguiente</span><span class="sxs-lookup"><span data-stu-id="448e0-153">Next step</span></span>

<span data-ttu-id="448e0-154">Cuando esté preparado para implementar la sincronización de directorios para su organización, vea [Implementar la sincronización de directorios de Office 365 en Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span><span class="sxs-lookup"><span data-stu-id="448e0-154">When you are ready to deploy directory synchronization for your organization, see [Deploy Office 365 directory synchronization in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="448e0-155">Vea también</span><span class="sxs-lookup"><span data-stu-id="448e0-155">See Also</span></span>

<span data-ttu-id="448e0-156">[Guías del entorno de pruebas de adopción de la nube (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
[Configuración básica del entorno de desarrollo y pruebas](base-configuration-dev-test-environment.md)
[Entorno de desarrollo y pruebas de Office 365](office-365-dev-test-environment.md)
[Cloud App Security para el entorno de desarrollo y pruebas de Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
[Protección contra amenazas avanzada en el entorno de desarrollo y pruebas de Office 365](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
[Adopción de la nube y soluciones híbridas](cloud-adoption-and-hybrid-solutions.md)</span><span class="sxs-lookup"><span data-stu-id="448e0-156">[Cloud adoption Test Lab Guides (TLGs)](cloud-adoption-test-lab-guides-tlgs.md)
[Base Configuration dev/test environment](base-configuration-dev-test-environment.md)
[Office 365 dev/test environment](office-365-dev-test-environment.md)
[Cloud App Security for your Office 365 dev/test environment](cloud-app-security-for-your-office-365-dev-test-environment.md)
[Advanced Threat Protection for your Office 365 dev/test environment](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
[Cloud adoption and hybrid solutions](cloud-adoption-and-hybrid-solutions.md)</span></span>




