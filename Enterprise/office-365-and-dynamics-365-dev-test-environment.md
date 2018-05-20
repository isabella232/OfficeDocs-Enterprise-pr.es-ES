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
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Ent_TLGs
ms.assetid: 098c1a1d-83a1-40eb-bbc9-47de7af8bb23
description: 'Resumen: Use esta guía de laboratorio de prueba para agregar Dynamics 365 a su entorno de desarrollo y prueba de Office 365.'
ms.openlocfilehash: 00d5cc0fd347aff7e201056f6af9ca271008d285
ms.sourcegitcommit: 8fcf6fd9f0c45a5445654ef811410fca3f4f5512
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2018
---
# <a name="office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="a2b9a-103">Entorno de desarrollo y pruebas de Office 365 y Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="a2b9a-103">Office 365 and Dynamics 365 dev/test environment</span></span>

 <span data-ttu-id="a2b9a-104">**Resumen:** Use esta guía de laboratorio de prueba para agregar Dynamics 365 a su entorno de desarrollo y prueba de Office 365.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-104">**Summary:** Use this Test Lab Guide to add Dynamics 365 to your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="a2b9a-105">Con las instrucciones de este artículo, agregará una suscripción de prueba a Dynamics 365 en la misma organización que su entorno de desarrollo y pruebas de Office 365 y creará un entorno de pruebas y desarrollo de Office 365 y Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-105">With the instructions in this article, you add a Dynamics 365 trial subscription to the same organization as your Office 365 dev/test environment, creating an Office 365 and Dynamics 365 dev/test environment.</span></span>

![Entorno de desarrollo y pruebas de Office 365 y Dynamics 365](images/o365-dynamics365-dev-test.png)
  
  
<span data-ttu-id="a2b9a-p101">Puede usar una suscripción de prueba a Dynamics 365 para probar las características y funcionalidades de Dynamics 365. Las siguientes soluciones se incluyen con la prueba de Dynamics 365 Plan 1, Enterprise Edition:</span><span class="sxs-lookup"><span data-stu-id="a2b9a-p101">You can use a Dynamics 365 trial subscription to demonstrate features and capabilities of Dynamics 365. The following solutions are included with a Dynamics 365 Plan 1, Enterprise Edition trial:</span></span>
  
- <span data-ttu-id="a2b9a-p102">[Microsoft Dynamics 365 para ventas](https://www.microsoft.com/dynamics365/sales). Aumentar las ventas con automatización e inteligencia digital ayudar a los vendedores centrarse y trabajar de manera más eficaz.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-p102">[Microsoft Dynamics 365 for Sales](https://www.microsoft.com/dynamics365/sales). Increase your sales with automation and digital intelligence helping your salespeople stay focused and work smarter.</span></span>
    
- <span data-ttu-id="a2b9a-p103">[Microsoft Dynamics 365 para el servicio al cliente](https://www.microsoft.com/dynamics365/customer-service). Ganar fidelidad proporcionando a los agentes de la información completa e inteligencia digital que necesitan para proporcionar un servicio sin problemas.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-p103">[Microsoft Dynamics 365 for Customer Service](https://www.microsoft.com/dynamics365/customer-service). Earn loyalty by giving your agents the complete information and digital intelligence they need to provide seamless service.</span></span>
    
- <span data-ttu-id="a2b9a-p104">[Microsoft Dynamics 365 para el servicio de campo](https://www.microsoft.com/dynamics365/field-service). Maestro de la llamada de servicio por optimizar sus programaciones, equipamiento de sus empleados y uso de herramientas predictivas para aumentar las ganancias.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-p104">[Microsoft Dynamics 365 for Field Service](https://www.microsoft.com/dynamics365/field-service). Master the service call by optimizing your schedules, equipping your workforce, and using predictive tools to increase profit.</span></span>
    
- <span data-ttu-id="a2b9a-p105">[Microsoft Dynamics 365 para la automatización de servicio de Project](https://www.microsoft.com/en-us/dynamics365/project-service-automation). Completar correctamente los proyectos y crear relaciones rentables con los empleados a ser productivos y herramientas inteligentes.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-p105">[Microsoft Dynamics 365 for Project Service Automation](https://www.microsoft.com/en-us/dynamics365/project-service-automation). Complete your projects successfully and create profitable relationships with productive employees and intelligent tools.</span></span>
    
<span data-ttu-id="a2b9a-117">Puede explorar uno o más de los servicios anteriores para usar en su suscripción de prueba a Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-117">You can explore one or more of the above for your Dynamics 365 trial subscription.</span></span>
  
![Guías del laboratorio de pruebas de Microsoft Cloud](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="a2b9a-119">Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual de todos los artículos en la pila de la Guía del entorno de pruebas de One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-119">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="a2b9a-120">Fase 1: Crear un entorno de desarrollo y pruebas ligero o de una empresa simulada de Office 365</span><span class="sxs-lookup"><span data-stu-id="a2b9a-120">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="a2b9a-121">Si desea probar Office 365 y Dynamics 365 en una forma sencilla con los requisitos mínimos, siga las instrucciones que aparecen en las fases 2 y 3 del [entorno de desarrollo y prueba de Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="a2b9a-121">If you just want to test Office 365 and Dynamics 365 in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="a2b9a-122">Si desea probar Office 365 y Dynamics 365 para una empresa simulada, siga las instrucciones que aparecen en la [sincronización de directorios para el entorno de desarrollo y prueba de Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="a2b9a-122">If you want to test Office 365 and Dynamics 365 for a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>

![El entorno de desarrollo y pruebas de Office 365](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
> [!NOTE]
> <span data-ttu-id="a2b9a-p106">La configuración recogida en este artículo no requiere el entorno de desarrollo y pruebas de una empresa simulada, que incluye una intranet simulada conectada a Internet y la sincronización de directorios para un bosque de Windows Server AD. Aquí se ofrece como opción para que pueda experimentar con Office 365 y Dynamics 365 en un entorno que representa una organización típica.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-p106">The configuration in this article does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can experiment with Office 365 and Dynamics 365 in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-add-a-dynamics-365-trial-subscription"></a><span data-ttu-id="a2b9a-126">Fase 2: Agregar una suscripción de prueba a Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="a2b9a-126">Phase 2: Add a Dynamics 365 trial subscription</span></span>

<span data-ttu-id="a2b9a-127">En esta fase, se registrará en la suscripción de prueba a Dynamics 365 y la agregará a la misma organización que su suscripción de prueba a Office 365.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-127">In this phase, you sign up for the Dynamics 365 trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
### <a name="sign-up-for-a-dynamics-365-trial-subscription"></a><span data-ttu-id="a2b9a-128">Registrarse para obtener una suscripción de prueba a Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="a2b9a-128">Sign up for a Dynamics 365 trial subscription</span></span>

1. <span data-ttu-id="a2b9a-129">Mediante un explorador en cualquiera de su equipo de escritorio (ligero) o desde CLIENT1 (simulado enterprise), inicie sesión el portal de Office 365 en [https://portal.office.com](https://portal.office.com) con las credenciales de su cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-129">Using a browser on either your desktop computer (lightweight) or from CLIENT1 (simulated enterprise), sign in to the Office 365 portal at [https://portal.office.com](https://portal.office.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="a2b9a-130">Haga clic en el icono **Administración**.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-130">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="a2b9a-131">En la pestaña **Centro de administración de Office**, en el panel de navegación izquierdo, haga clic en **Facturación > Servicios de compra**.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-131">On the **Office admin center** tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="a2b9a-p107">En la página **Servicios de compra**, busque el elemento **Dynamics 365 (plan 1) Enterprise Edition**. Mantenga el puntero del mouse sobre ese elemento y haga clic en **Iniciar prueba gratuita**.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-p107">On the **Purchase services** page, find the **Dynamics 365 Plan 1 Enterprise Edition** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="a2b9a-134">En la página **Confirmar pedido**, haga clic en **Probar ahora**.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-134">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="a2b9a-135">En la página **Recibo del pedido**, haga clic en **Continuar**.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-135">On the **Order receipt** page, click **Continue**.</span></span>

![Entorno de desarrollo y pruebas de Office 365 y Dynamics 365](images/o365-dynamics365-dev-test.png)
    
> [!NOTE]
> <span data-ttu-id="a2b9a-p108">La suscripción de prueba de Dynamics 365 Plan 1 Enterprise Edition es de 30 días. Puede extender fácilmente la suscripción de prueba otros 30 días. Para un entorno de pruebas y desarrollo permanente, cree una nueva suscripción de pago con un número reducido de licencias.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-p108">The Dynamics 365 Plan 1 Enterprise Edition trial subscription is 30 days. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
## <a name="phase-3-assign-dynamics-365-licenses-and-system-administrators"></a><span data-ttu-id="a2b9a-140">Fase 3: Asignar licencias Dynamics 365 y administradores del sistema</span><span class="sxs-lookup"><span data-stu-id="a2b9a-140">Phase 3: Assign Dynamics 365 licenses and system administrators</span></span>

<span data-ttu-id="a2b9a-141">En esta fase, asignará las licencias de Dynamics 365 al administrador global y a las cuentas Usuario 2 y Usuario 3, y los hará administradores del sistema.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-141">In this phase, you assign Dynamics 365 licenses to the global administrator, User 2, and User 3 accounts and make them system administrators.</span></span>
  
<span data-ttu-id="a2b9a-142">Siga estos pasos para asignar licencias de Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-142">Use these steps to assign Dynamics 365 licenses.</span></span>
  
1. <span data-ttu-id="a2b9a-143">En la pestaña **Centro de administración de Office**, haga clic en **Usuarios > Usuarios activos**.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-143">On the **Office admin center** tab, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="a2b9a-144">En la lista de usuarios activos, haga clic en su cuenta de administrador global y, después, haga clic en **Editar** en **Licencias de productos**.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-144">In the list of active users, click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="a2b9a-145">	En el panel **Licencias de productos**, cambie la licencia del producto de **Dynamics 365 (plan 1) Enterprise Edition** a **Activada**, seleccione **Guardar** y, después, haga clic en **Cerrar** dos veces.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-145">On the **Product licenses** pane, turn the product license for **Dynamics 365 Plan 1 Enterprise Edition** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="a2b9a-146">Realice los pasos 2 y 3 para las cuentas Usuario 2 y Usuario 3.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-146">Perform steps 2 and 3 for the User 2 and User 3 accounts.</span></span>
    
5. <span data-ttu-id="a2b9a-147">Cierre la pestaña **Centro de administración de Office**.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-147">Close the **Office admin center** tab.</span></span>
    
<span data-ttu-id="a2b9a-148">Siga estos pasos para configurar las cuentas Usuario 2 y Usuario 3 como administradores del sistema de Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-148">Use these steps to configure the User 2 and User 3 accounts as Dynamics 365 system administrators.</span></span>
  
1. <span data-ttu-id="a2b9a-149">En la ficha **Página principal de Microsoft Office** , haga clic en **Admin**.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-149">From the **Microsoft Office Home** tab, click **Admin**.</span></span>
    
2. <span data-ttu-id="a2b9a-150">En la ficha del **Centro de administración de Office** , en el panel de navegación izquierdo, haga clic en **centros de administración**y, a continuación, haga clic en **Dynamics 365**.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-150">On the **Office Admin center** tab, in the left navigation, click **Admin centers**, and then click **Dynamics 365**.</span></span>
    
    <span data-ttu-id="a2b9a-151">Es posible que tenga que esperar hasta que finalice el aprovisionamiento de Dynamics 365 para que este aparezca en el menú.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-151">You may need to wait for Dynamics 365 to finish provisioning before Dynamics 365 appears in the menu.</span></span>
    
3. <span data-ttu-id="a2b9a-152">En la pestaña Dynamics 365, haga clic en **Todos estos** y, después, en **Finalizar configuración**.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-152">On the Dynamics 365 tab, click **All of these**, and then click **Complete Setup.**</span></span>
    
    <span data-ttu-id="a2b9a-153">Espere a que se complete la configuración.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-153">Wait for setup to complete.</span></span>
    
    <span data-ttu-id="a2b9a-p109">Cuando se complete la configuración, se mostrará un Panel de actividad de ventas basado en datos de ejemplo que forman parte de la suscripción de prueba. Dedique unos minutos a ver el vídeo **Bienvenido a la prueba**. Cuando se complete, cierra la ventana del vídeo.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-p109">When setup completes, it displays a Sales Activity Dashboard based on sample data that is part of the trail subscription. Take a few moments to view the **Welcome to your trial** video. Close the video window when complete.</span></span>
    
4. <span data-ttu-id="a2b9a-157">En la barra de herramientas de la parte superior, haga clic en la flecha abajo junto a **Ventas**, seleccione **Configuración** y, después, haga clic en **Seguridad**.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-157">On the toolbar at the top, click the down arrow next to **Sales**, click **Settings**, and then click **Security**.</span></span>
    
5. <span data-ttu-id="a2b9a-158">En la página **Seguridad**, haga clic en **Usuarios**.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-158">On the **Security** page, click **Users**.</span></span>
    
6. <span data-ttu-id="a2b9a-159">En la lista de usuarios, haga clic en **Usuario 2**.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-159">In the list of users, click **User 2**.</span></span>
    
7. <span data-ttu-id="a2b9a-160">En la barra de herramientas, haga clic en **Administrar roles**.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-160">In the tool bar, click **Manage Roles**.</span></span>
    
8. <span data-ttu-id="a2b9a-161">En **Administrar roles**, haga clic en **Administrador del sistema** y, después, en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-161">In **Manage Roles**, click **System Administrator**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="a2b9a-162">En la barra de herramientas de la parte superior, haga clic en **Seguridad**.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-162">In the tool bar at the top click **Security**.</span></span>
    
10. <span data-ttu-id="a2b9a-163">Repita los pasos del 5 al 8 para la cuenta Usuario 3.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-163">Repeat steps 5-8 for the User 3 account.</span></span>
    
11. <span data-ttu-id="a2b9a-164">Cierre la pestaña **Usuario: Usuario3**.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-164">Close the **User: User3** tab.</span></span>
    
> [!NOTE]
> <span data-ttu-id="a2b9a-165">El rol de administrador del sistema de Dynamics 365 se asignó automáticamente a su cuenta de administrador global de Office 365.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-165">Your Office 365 global administrator account was automatically assigned the Dynamics 365 system administrator role.</span></span> 
  
<span data-ttu-id="a2b9a-166">El entorno de desarrollo y pruebas de Office 365 y Dynamics 365 ahora tiene lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="a2b9a-166">Your Office 365 and Dynamics 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="a2b9a-167">Suscripciones de prueba a Office 365 E5 Enterprise y a Dynamics 365 que comparten la misma organización y el mismo inquilino de Azure AD con su lista de cuentas de usuario.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-167">Office 365 E5 Enterprise and Dynamics 365 trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="a2b9a-168">Sus cuentas de administrador de organización global, Usuario 2 y Usuario 3 están habilitadas para usar Office 365 Enterprise E5 y Dynamics 365, y son administradores del sistema de Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="a2b9a-168">Your global enterprise administrator, User 2, and User 3 accounts are enabled to use both Office 365 E5 Enterprise and Dynamics 365 and are Dynamics 365 system administrators.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="a2b9a-169">Paso siguiente</span><span class="sxs-lookup"><span data-stu-id="a2b9a-169">Next step</span></span>

<span data-ttu-id="a2b9a-170">Configurar y, a continuación, demuestre cómo Office 365 y Dynamics 365 funcionan conjuntamente los buzones de correo de Exchange Online con la [integración de Exchange Online para el entorno de desarrollo y prueba de Office 365 y Dynamics 365](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md).</span><span class="sxs-lookup"><span data-stu-id="a2b9a-170">Configure and then demonstrate how Office 365 and Dynamics 365 work together in Exchange Online mailboxes with [Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a2b9a-171">Vea también</span><span class="sxs-lookup"><span data-stu-id="a2b9a-171">See Also</span></span>

[<span data-ttu-id="a2b9a-172">Guías del laboratorio de pruebas de adopción de la nube (TLG)</span><span class="sxs-lookup"><span data-stu-id="a2b9a-172">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="a2b9a-173">Entorno de desarrollo y pruebas de la configuración básica</span><span class="sxs-lookup"><span data-stu-id="a2b9a-173">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="a2b9a-174">Entorno de desarrollo y prueba de Office 365</span><span class="sxs-lookup"><span data-stu-id="a2b9a-174">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="a2b9a-175">Sincronización de directorios (DirSync) para el entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="a2b9a-175">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)

[<span data-ttu-id="a2b9a-176">Administración de suscripción para Dynamics 365 (online)</span><span class="sxs-lookup"><span data-stu-id="a2b9a-176">Subscription Management for Dynamics 365 (online)</span></span>](https://technet.microsoft.com/library/jj679903.aspx)
  
[<span data-ttu-id="a2b9a-177">Administración de Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="a2b9a-177">Administering Dynamics 365</span></span>](https://technet.microsoft.com/library/dn531101.aspx)


