---
title: Entorno de desarrollo y pruebas de Office 365 y Dynamics 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Ent_TLGs
ms.assetid: 098c1a1d-83a1-40eb-bbc9-47de7af8bb23
description: 'Resumen: Use esta Guía del laboratorio de pruebas para agregar Dynamics 365 al entorno de desarrollo y pruebas de Office 365.'
ms.openlocfilehash: 9e4c98129c68ab5d2f0d9fc486ab62740c625af5
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "30574064"
---
# <a name="office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="eeb48-103">Entorno de desarrollo y pruebas de Office 365 y Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="eeb48-103">Office 365 and Dynamics 365 dev/test environment</span></span>

 <span data-ttu-id="eeb48-104">**Resumen:** Use esta Guía del laboratorio de pruebas para agregar Dynamics 365 al entorno de desarrollo y pruebas de Office 365.</span><span class="sxs-lookup"><span data-stu-id="eeb48-104">**Summary:** Use this Test Lab Guide to add Dynamics 365 to your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="eeb48-105">Con las instrucciones de este artículo, agregará una suscripción de prueba a Dynamics 365 en la misma organización que su entorno de desarrollo y pruebas de Office 365 y creará un entorno de pruebas y desarrollo de Office 365 y Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="eeb48-105">With the instructions in this article, you add a Dynamics 365 trial subscription to the same organization as your Office 365 dev/test environment, creating an Office 365 and Dynamics 365 dev/test environment.</span></span>

![Entorno de desarrollo y pruebas de Office 365 y Dynamics 365](media/o365-dynamics365-dev-test.png)
  
  
<span data-ttu-id="eeb48-p101">Puede usar una suscripción de prueba a Dynamics 365 para probar las características y funcionalidades de Dynamics 365. Las siguientes soluciones se incluyen con la prueba de Dynamics 365 Plan 1, Enterprise Edition:</span><span class="sxs-lookup"><span data-stu-id="eeb48-p101">You can use a Dynamics 365 trial subscription to demonstrate features and capabilities of Dynamics 365. The following solutions are included with a Dynamics 365 Plan 1, Enterprise Edition trial:</span></span>
  
- <span data-ttu-id="eeb48-p102">[Microsoft Dynamics 365 for Sales](https://www.microsoft.com/dynamics365/sales). Aumente sus ventas con la inteligencia de automatización y digital, lo que ayudará a los vendedores a concentrarse más y a trabajar mejor.</span><span class="sxs-lookup"><span data-stu-id="eeb48-p102">[Microsoft Dynamics 365 for Sales](https://www.microsoft.com/dynamics365/sales). Increase your sales with automation and digital intelligence helping your salespeople stay focused and work smarter.</span></span>
    
- <span data-ttu-id="eeb48-p103">[Microsoft Dynamics 365 for Customer Service](https://www.microsoft.com/dynamics365/customer-service). Gane fidelidad proporcionando a sus agentes la información completa y la inteligencia digital que necesitan para proporcionar el servicio sin problemas.</span><span class="sxs-lookup"><span data-stu-id="eeb48-p103">[Microsoft Dynamics 365 for Customer Service](https://www.microsoft.com/dynamics365/customer-service). Earn loyalty by giving your agents the complete information and digital intelligence they need to provide seamless service.</span></span>
    
- <span data-ttu-id="eeb48-p104">[Microsoft Dynamics 365 for Field Service](https://www.microsoft.com/dynamics365/field-service). Domine las llamadas del servicio optimizando sus programaciones, equipando a sus recursos y usando herramientas predictivas para aumentar las ganancias.</span><span class="sxs-lookup"><span data-stu-id="eeb48-p104">[Microsoft Dynamics 365 for Field Service](https://www.microsoft.com/dynamics365/field-service). Master the service call by optimizing your schedules, equipping your workforce, and using predictive tools to increase profit.</span></span>
    
- <span data-ttu-id="eeb48-p105">[Microsoft Dynamics 365 for Project Service Automation](https://www.microsoft.com/es-ES/dynamics365/project-service-automation). Complete con éxito sus proyectos y cree relaciones beneficiosas con empleados productivos y herramientas inteligentes.</span><span class="sxs-lookup"><span data-stu-id="eeb48-p105">[Microsoft Dynamics 365 for Project Service Automation](https://www.microsoft.com/es-ES/dynamics365/project-service-automation). Complete your projects successfully and create profitable relationships with productive employees and intelligent tools.</span></span>
    
<span data-ttu-id="eeb48-117">Puede explorar uno o más de los servicios anteriores para usar en su suscripción de prueba a Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="eeb48-117">You can explore one or more of the above for your Dynamics 365 trial subscription.</span></span>
  
![Guías del laboratorio de pruebas de Microsoft Cloud](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="eeb48-119">Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual de todos los artículos de la pila Guía de laboratorio de pruebas de One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="eeb48-119">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="eeb48-120">Fase 1: Crear un entorno de desarrollo y pruebas ligero o de una empresa simulada de Office 365</span><span class="sxs-lookup"><span data-stu-id="eeb48-120">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="eeb48-121">Si solo quiere probar Office 365 y Dynamics 365 de forma general y con los requisitos mínimos, siga las instrucciones indicadas en las fases 2 y 3 del [Entorno de desarrollo y pruebas de Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="eeb48-121">If you just want to test Office 365 and Dynamics 365 in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="eeb48-122">Si quiere probar Office 365 y Dynamics 365 para una empresa simulada, siga las instrucciones indicadas en [Sincronización de directorios (DirSync) para el entorno de desarrollo y pruebas de Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="eeb48-122">If you want to test Office 365 and Dynamics 365 for a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>

![El entorno de desarrollo y pruebas de Office 365](media/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
> [!NOTE]
> <span data-ttu-id="eeb48-p106">La configuración recogida en este artículo no requiere el entorno de desarrollo y pruebas de una empresa simulada, que incluye una intranet simulada conectada a Internet y la sincronización de directorios para un bosque de Windows Server AD. Aquí se ofrece como opción para que pueda experimentar con Office 365 y Dynamics 365 en un entorno que representa una organización típica.</span><span class="sxs-lookup"><span data-stu-id="eeb48-p106">The configuration in this article does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can experiment with Office 365 and Dynamics 365 in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-add-a-dynamics-365-trial-subscription"></a><span data-ttu-id="eeb48-126">Fase 2: Agregar una suscripción de prueba a Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="eeb48-126">Phase 2: Add a Dynamics 365 trial subscription</span></span>

<span data-ttu-id="eeb48-127">En esta fase, se registrará en la suscripción de prueba a Dynamics 365 y la agregará a la misma organización que su suscripción de prueba a Office 365.</span><span class="sxs-lookup"><span data-stu-id="eeb48-127">In this phase, you sign up for the Dynamics 365 trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
### <a name="sign-up-for-a-dynamics-365-trial-subscription"></a><span data-ttu-id="eeb48-128">Registrarse para obtener una suscripción de prueba a Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="eeb48-128">Sign up for a Dynamics 365 trial subscription</span></span>

1. <span data-ttu-id="eeb48-129">Con un explorador con un equipo de escritorio (ligero) o desde CLIENTE1 (empresa simulada), inicie sesión en el Centro de administración de Microsoft 365 en [https://admin.microsoft.com](https://admin.microsoft.com) con las credenciales de la cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="eeb48-129">Using a browser on either your desktop computer (lightweight) or from CLIENT1 (simulated enterprise), sign in to the Office 365 portal at [https://admin.microsoft.com](https://admin.microsoft.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="eeb48-130">Haga clic en el icono **Administración**.</span><span class="sxs-lookup"><span data-stu-id="eeb48-130">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="eeb48-131">En la pestaña **Centro de administración de Microsoft 365**, en el panel de navegación izquierdo, haga clic en **Facturación > Servicios de compra**.</span><span class="sxs-lookup"><span data-stu-id="eeb48-131">On the **Microsoft 365 admin center** tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="eeb48-p107">En la página **Servicios de compra**, busque el elemento **Dynamics 365 (plan 1) Enterprise Edition**. Mantenga el puntero del mouse sobre ese elemento y haga clic en **Iniciar prueba gratuita**.</span><span class="sxs-lookup"><span data-stu-id="eeb48-p107">On the **Purchase services** page, find the **Dynamics 365 Plan 1 Enterprise Edition** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="eeb48-134">En la página **Confirmar pedido**, haga clic en **Probar ahora**.</span><span class="sxs-lookup"><span data-stu-id="eeb48-134">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="eeb48-135">En la página **Recibo del pedido**, haga clic en **Continuar**.</span><span class="sxs-lookup"><span data-stu-id="eeb48-135">On the **Order receipt** page, click **Continue**.</span></span>

![Entorno de desarrollo y pruebas de Office 365 y Dynamics 365](media/o365-dynamics365-dev-test.png)
    
> [!NOTE]
> <span data-ttu-id="eeb48-p108">La suscripción de prueba de Dynamics 365 Plan 1 Enterprise Edition es de 30 días. Puede extender fácilmente la suscripción de prueba otros 30 días. Para un entorno de pruebas y desarrollo permanente, cree una nueva suscripción de pago con un número reducido de licencias.</span><span class="sxs-lookup"><span data-stu-id="eeb48-p108">The Dynamics 365 Plan 1 Enterprise Edition trial subscription is 30 days. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
## <a name="phase-3-assign-dynamics-365-licenses-and-system-administrators"></a><span data-ttu-id="eeb48-140">Fase 3: Asignar licencias Dynamics 365 y administradores del sistema</span><span class="sxs-lookup"><span data-stu-id="eeb48-140">Phase 3: Assign Dynamics 365 licenses and system administrators</span></span>

<span data-ttu-id="eeb48-141">En esta fase, asignará las licencias de Dynamics 365 al administrador global y a las cuentas Usuario 2 y Usuario 3, y los hará administradores del sistema.</span><span class="sxs-lookup"><span data-stu-id="eeb48-141">In this phase, you assign Dynamics 365 licenses to the global administrator, User 2, and User 3 accounts and make them system administrators.</span></span>
  
<span data-ttu-id="eeb48-142">Siga estos pasos para asignar licencias de Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="eeb48-142">Use these steps to assign Dynamics 365 licenses.</span></span>
  
1. <span data-ttu-id="eeb48-143">En la pestaña **Centro de administración de Microsoft 365**, haga clic en **Usuarios > Usuarios activos**.</span><span class="sxs-lookup"><span data-stu-id="eeb48-143">On the **Microsoft 365 admin center** tab, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="eeb48-144">En la lista de usuarios activos, haga clic en su cuenta de administrador global y, después, haga clic en **Editar** en **Licencias de productos**.</span><span class="sxs-lookup"><span data-stu-id="eeb48-144">In the list of active users, click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="eeb48-145">	En el panel *\*Licencias de productos*\*, cambie la licencia del producto de *\*Dynamics 365 (plan 1) Enterprise Edition** a *\*Activada*\*, seleccione *\*Guardar** y, después, haga clic en *\*Cerrar** dos veces.</span><span class="sxs-lookup"><span data-stu-id="eeb48-145">On the **Product licenses** pane, turn the product license for **Dynamics 365 Plan 1 Enterprise Edition** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="eeb48-146">Realice los pasos 2 y 3 para las cuentas Usuario 2 y Usuario 3.</span><span class="sxs-lookup"><span data-stu-id="eeb48-146">Perform steps 2 and 3 for the User 2 and User 3 accounts.</span></span>
    
5. <span data-ttu-id="eeb48-147">Cierre la pestaña del **Centro de administración de Microsoft 365**.</span><span class="sxs-lookup"><span data-stu-id="eeb48-147">Close the **Microsoft 365 admin center** tab.</span></span>
    
<span data-ttu-id="eeb48-148">Siga estos pasos para configurar las cuentas Usuario 2 y Usuario 3 como administradores del sistema de Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="eeb48-148">Use these steps to configure the User 2 and User 3 accounts as Dynamics 365 system administrators.</span></span>
  
1. <span data-ttu-id="eeb48-149">En la pestaña **Página principal de Microsoft Office**, haga clic en **Administración**.</span><span class="sxs-lookup"><span data-stu-id="eeb48-149">From the **Microsoft Office Home** tab, click **Admin**.</span></span>
    
2. <span data-ttu-id="eeb48-150">En la pestaña **Centro de administración de Office**, en el panel de navegación izquierdo, haga clic en **Centros de administración** y, después, seleccione **Dynamics 365**.</span><span class="sxs-lookup"><span data-stu-id="eeb48-150">On the **Office Admin center** tab, in the left navigation, click **Admin centers**, and then click **Dynamics 365**.</span></span>
    
    <span data-ttu-id="eeb48-151">Es posible que tenga que esperar hasta que finalice el aprovisionamiento de Dynamics 365 para que este aparezca en el menú.</span><span class="sxs-lookup"><span data-stu-id="eeb48-151">You may need to wait for Dynamics 365 to finish provisioning before Dynamics 365 appears in the menu.</span></span>
    
3. <span data-ttu-id="eeb48-152">En la pestaña Dynamics 365, haga clic en **Todos estos** y, después, en **Finalizar configuración**.</span><span class="sxs-lookup"><span data-stu-id="eeb48-152">On the Dynamics 365 tab, click **All of these**, and then click **Complete Setup.**</span></span>
    
    <span data-ttu-id="eeb48-153">Espere a que se complete la configuración.</span><span class="sxs-lookup"><span data-stu-id="eeb48-153">Wait for setup to complete.</span></span>
    
    <span data-ttu-id="eeb48-p109">Cuando se complete la configuración, se mostrará un Panel de actividad de ventas basado en datos de ejemplo que forman parte de la suscripción de prueba. Dedique unos minutos a ver el vídeo **Bienvenido a la prueba**. Cuando se complete, cierra la ventana del vídeo.</span><span class="sxs-lookup"><span data-stu-id="eeb48-p109">When setup completes, it displays a Sales Activity Dashboard based on sample data that is part of the trail subscription. Take a few moments to view the **Welcome to your trial** video. Close the video window when complete.</span></span>
    
4. <span data-ttu-id="eeb48-157">En la barra de herramientas de la parte superior, haga clic en la flecha abajo junto a **Ventas**, seleccione **Configuración** y, después, haga clic en **Seguridad**.</span><span class="sxs-lookup"><span data-stu-id="eeb48-157">On the toolbar at the top, click the down arrow next to **Sales**, click **Settings**, and then click **Security**.</span></span>
    
5. <span data-ttu-id="eeb48-158">En la página **Seguridad**, haga clic en **Usuarios**.</span><span class="sxs-lookup"><span data-stu-id="eeb48-158">On the **Security** page, click **Users**.</span></span>
    
6. <span data-ttu-id="eeb48-159">En la lista de usuarios, haga clic en **Usuario 2**.</span><span class="sxs-lookup"><span data-stu-id="eeb48-159">In the list of users, click **User 2**.</span></span>
    
7. <span data-ttu-id="eeb48-160">En la barra de herramientas, haga clic en **Administrar roles**.</span><span class="sxs-lookup"><span data-stu-id="eeb48-160">In the tool bar, click **Manage Roles**.</span></span>
    
8. <span data-ttu-id="eeb48-161">En **Administrar roles**, haga clic en **Administrador del sistema** y, después, en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="eeb48-161">In **Manage Roles**, click **System Administrator**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="eeb48-162">En la barra de herramientas de la parte superior, haga clic en **Seguridad**.</span><span class="sxs-lookup"><span data-stu-id="eeb48-162">In the tool bar at the top click **Security**.</span></span>
    
10. <span data-ttu-id="eeb48-163">Repita los pasos del 5 al 8 para la cuenta Usuario 3.</span><span class="sxs-lookup"><span data-stu-id="eeb48-163">Repeat steps 5-8 for the User 3 account.</span></span>
    
11. <span data-ttu-id="eeb48-164">Cierre la pestaña **Usuario: Usuario3**.</span><span class="sxs-lookup"><span data-stu-id="eeb48-164">Close the **User: User3** tab.</span></span>
    
> [!NOTE]
> <span data-ttu-id="eeb48-165">El rol de administrador del sistema de Dynamics 365 se asignó automáticamente a su cuenta de administrador global de Office 365.</span><span class="sxs-lookup"><span data-stu-id="eeb48-165">Your Office 365 global administrator account was automatically assigned the Dynamics 365 system administrator role.</span></span> 
  
<span data-ttu-id="eeb48-166">El entorno de desarrollo y pruebas de Office 365 y Dynamics 365 ahora tiene lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="eeb48-166">Your Office 365 and Dynamics 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="eeb48-167">Suscripciones de prueba a Office 365 E5 Enterprise y a Dynamics 365 que comparten la misma organización y el mismo inquilino de Azure AD con su lista de cuentas de usuario.</span><span class="sxs-lookup"><span data-stu-id="eeb48-167">Office 365 E5 Enterprise and Dynamics 365 trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="eeb48-168">Sus cuentas de administrador de organización global, Usuario 2 y Usuario 3 están habilitadas para usar Office 365 Enterprise E5 y Dynamics 365, y son administradores del sistema de Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="eeb48-168">Your global enterprise administrator, User 2, and User 3 accounts are enabled to use both Office 365 E5 Enterprise and Dynamics 365 and are Dynamics 365 system administrators.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="eeb48-169">Paso siguiente</span><span class="sxs-lookup"><span data-stu-id="eeb48-169">Next step</span></span>

<span data-ttu-id="eeb48-170">Configure y muestre cómo Office 365 y Dynamics 365 colaboran en los buzones de Exchange Online con la [Integración de Exchange Online para su entorno de desarrollo y pruebas de Office 365 y Dynamics 365](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md).</span><span class="sxs-lookup"><span data-stu-id="eeb48-170">Configure and then demonstrate how Office 365 and Dynamics 365 work together in Exchange Online mailboxes with [Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="eeb48-171">Vea también</span><span class="sxs-lookup"><span data-stu-id="eeb48-171">See Also</span></span>

[<span data-ttu-id="eeb48-172">Guías del laboratorio de pruebas de adopción de la nube (TLG)</span><span class="sxs-lookup"><span data-stu-id="eeb48-172">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="eeb48-173">Entorno de desarrollo y pruebas de la configuración básica</span><span class="sxs-lookup"><span data-stu-id="eeb48-173">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="eeb48-174">Entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="eeb48-174">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="eeb48-175">Sincronización de directorios (DirSync) para el entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="eeb48-175">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)

[<span data-ttu-id="eeb48-176">Administración de suscripción para Dynamics 365 (online)</span><span class="sxs-lookup"><span data-stu-id="eeb48-176">Subscription Management for Dynamics 365 (online)</span></span>](https://technet.microsoft.com/library/jj679903.aspx)
  
[<span data-ttu-id="eeb48-177">Administración de Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="eeb48-177">Administering Dynamics 365</span></span>](https://technet.microsoft.com/library/dn531101.aspx)


