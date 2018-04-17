---
title: El entorno de desarrollo y prueba de una nube de Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: a1370fe4-2fd6-4fea-ad1d-3555433d6d2e
description: 'Resumen: Utilice a esta guía de laboratorio de prueba para crear un entorno de pruebas y desarrollo que incluye todas las ofertas de nube de Microsoft.'
ms.openlocfilehash: c1d0e190e6d7e3871cf4289729b53cc0b4b5d04d
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="the-one-microsoft-cloud-devtest-environment"></a><span data-ttu-id="1612d-103">El entorno de desarrollo y prueba de una nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="1612d-103">The One Microsoft Cloud dev/test environment</span></span>

 <span data-ttu-id="1612d-104">**Resumen:** Utilice a esta guía de laboratorio de prueba para crear un entorno de pruebas y desarrollo que incluye todas las ofertas de nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1612d-104">**Summary:** Use this Test Lab Guide to create a dev/test environment that includes all of Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="1612d-p101">Con las instrucciones de este artículo, crear una intranet simulada en los servicios de infraestructura de Microsoft Azure y luego agregar Microsoft Office 365, Microsoft Enterprise Mobility + seguridad (EMS) y Microsoft Dynamics 365 suscripciones. El resultado es una organización simplificada que utiliza las ofertas de nube de Microsoft todas al mismo tiempo en un entorno de pruebas y desarrollo único.</span><span class="sxs-lookup"><span data-stu-id="1612d-p101">With the instructions in this article, you create a simulated intranet in Microsoft Azure infrastructure services and then add Microsoft Office 365, Microsoft Enterprise Mobility + Security (EMS), and Microsoft Dynamics 365 subscriptions. The result is a simplified organization that uses all Microsoft's cloud offerings at the same time in a single dev/test environment.</span></span> 
  
![Fase 3 del entorno de pruebas y desarrollo de One Microsoft Cloud con Azure, Office 365, EMS y Dynamics 365](images/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
<span data-ttu-id="1612d-108">Puede utilizar la configuración resultante al:</span><span class="sxs-lookup"><span data-stu-id="1612d-108">You can use the resulting configuration to:</span></span>
  
- <span data-ttu-id="1612d-109">Experimente la integración a través de ofertas de nube de Microsoft, tales como la infraestructura de identidad común proporcionada por Azure Active Directory (AD).</span><span class="sxs-lookup"><span data-stu-id="1612d-109">Experience the integration across Microsoft's cloud offerings, such as the common identity infrastructure provided by Azure Active Directory (AD).</span></span>
    
- <span data-ttu-id="1612d-110">Evaluar escenarios de end-to-end que incluyen múltiples ofertas de Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="1612d-110">Evaluate end-to-end scenarios that include multiple Microsoft Cloud offerings.</span></span>
    
- <span data-ttu-id="1612d-111">Crear una demostración, prueba de concepto o configuración de pruebas y desarrollo que utiliza múltiples ofertas de Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="1612d-111">Create a demo, proof-of-concept, or dev/test configuration that uses multiple Microsoft Cloud offerings.</span></span>
    
- <span data-ttu-id="1612d-112">Desarrollará sus habilidades de Microsoft Cloud para desarrollo profesional.</span><span class="sxs-lookup"><span data-stu-id="1612d-112">Build your Microsoft Cloud skills for professional development.</span></span>
    
## <a name="phase-1-create-a-simulated-intranet-and-add-office-365"></a><span data-ttu-id="1612d-113">Fase 1: Crear una intranet simulada y agregar Office 365</span><span class="sxs-lookup"><span data-stu-id="1612d-113">Phase 1: Create a simulated intranet and add Office 365</span></span>

<span data-ttu-id="1612d-114">Siga las instrucciones de [sincronización de directorios para el entorno de desarrollo y prueba de Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="1612d-114">Follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="1612d-115">La figura 1 muestra la configuración resultante, que incluye Office 365 y una intranet simulada ejecutando en servicios de infraestructura de Azure y sincronización de directorios desde un bosque de Windows Server Active Directory (AD) local.</span><span class="sxs-lookup"><span data-stu-id="1612d-115">Figure 1 shows your resulting configuration, which includes Office 365 and a simulated intranet running in Azure infrastructure services and directory synchronization from an on-premises Windows Server Active Directory (AD) forest.</span></span>
  
<span data-ttu-id="1612d-116">**Figura 1: La intranet simulada en Azure con Office 365**</span><span class="sxs-lookup"><span data-stu-id="1612d-116">**Figure 1: The simulated intranet in Azure with Office 365**</span></span>

![El entorno de desarrollo y prueba de Office 365 con DirSync](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
> [!NOTE]
> <span data-ttu-id="1612d-p102">La versión de prueba de Azure es de 30 días. La suscripción de prueba de Office 365 Enterprise E5 es 30 días, que se puede extender fácilmente para otro 30 días. Para un entorno de pruebas y desarrollo permanente, crear un nuevo pagado suscripción de Azure y una nueva suscripción de Office 365 Enterprise E5 pagada con un número pequeño de licencias.</span><span class="sxs-lookup"><span data-stu-id="1612d-p102">The Azure trial is 30 days. The Office 365 Enterprise E5 Trial subscription is 30 days, which can be easily extended for another 30 days. For a permanent dev/test environment, create a new paid Azure subscription and a new paid Office 365 Enterprise E5 subscription with a small number of licenses.</span></span> 
  
## <a name="phase-2-add-ems"></a><span data-ttu-id="1612d-121">Fase 2: Agregar EMS</span><span class="sxs-lookup"><span data-stu-id="1612d-121">Phase 2: Add EMS</span></span>

<span data-ttu-id="1612d-122">En esta fase, se inscribirá en la suscripción de prueba de EMS y la agregará a la misma organización que su suscripción de prueba de Office 365.</span><span class="sxs-lookup"><span data-stu-id="1612d-122">In this phase, you sign up for the EMS trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="1612d-123">Con un explorador ya sea el equipo de escritorio o desde CLIENTE1, iniciar sesión en el portal de Office 365 en [https://portal.office.com](https://portal.office.com) con las credenciales de la cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="1612d-123">With a browser on either your desktop computer or from CLIENT1, sign in to the Office 365 portal at [https://portal.office.com](https://portal.office.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="1612d-124">Haga clic en el icono **Administración**.</span><span class="sxs-lookup"><span data-stu-id="1612d-124">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="1612d-125">En la pestaña **Centro de administración de Office** del explorador, en el panel de navegación izquierdo, haga clic en **Facturación > Servicios de compra**.</span><span class="sxs-lookup"><span data-stu-id="1612d-125">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="1612d-p103">En la página **Servicios de compra** , busque el elemento de **seguridad E5 + de movilidad en la empresa** . Sitúe el puntero del mouse sobre él y haga clic en **iniciar la versión de prueba gratuita**.</span><span class="sxs-lookup"><span data-stu-id="1612d-p103">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="1612d-128">En la página **Confirmar pedido**, haga clic en **Probar ahora**.</span><span class="sxs-lookup"><span data-stu-id="1612d-128">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="1612d-129">En la página **Recibo del pedido**, haga clic en **Continuar**.</span><span class="sxs-lookup"><span data-stu-id="1612d-129">On the **Order receipt** page, click **Continue**.</span></span>
    
> [!NOTE]
> <span data-ttu-id="1612d-p104">La suscripción de prueba a Enterprise Mobility + Security E5 tiene una duración de 90 días. Si quiere usar un entorno de pruebas y desarrollo permanente, cree una nueva suscripción de pago con un número reducido de licencias.</span><span class="sxs-lookup"><span data-stu-id="1612d-p104">The Enterprise Mobility + Security E5 trial subscription is 90 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
<span data-ttu-id="1612d-132">A continuación, habilitar la movilidad en la empresa + licencia E5 de seguridad para todas las cuentas de usuario.</span><span class="sxs-lookup"><span data-stu-id="1612d-132">Next, enable the Enterprise Mobility + Security E5 license for all user accounts.</span></span>
  
1. <span data-ttu-id="1612d-133">En la pestaña **Centro de administración de Office 365** del explorador, en el panel de navegación izquierdo, haga clic en **Usuarios > Usuarios activos**.</span><span class="sxs-lookup"><span data-stu-id="1612d-133">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="1612d-134">Haga clic en la cuenta de administrador global y, a continuación, haga clic en **Editar** para **licencias de producto**.</span><span class="sxs-lookup"><span data-stu-id="1612d-134">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="1612d-135">En el panel de **licencias de producto** , activar la licencia del producto de **movilidad en la empresa + seguridad E5** en **On**, haga clic en **Guardar** y, a continuación, haga clic en **Cerrar** dos veces.</span><span class="sxs-lookup"><span data-stu-id="1612d-135">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="1612d-136">Para el resto de sus cuentas (Usuario 1, Usuario 2, Usuario 3, Usuario 4 y Usuario 5), complete los pasos 2 y 3.</span><span class="sxs-lookup"><span data-stu-id="1612d-136">For all of your other accounts (User1, User 2, User 3, User 4, and User 5), do steps 2 and 3.</span></span>
    
<span data-ttu-id="1612d-137">Ahora tiene su entorno de pruebas y desarrollo:</span><span class="sxs-lookup"><span data-stu-id="1612d-137">Your dev/test environment now has:</span></span>
  
- <span data-ttu-id="1612d-138">Intranet simulada que se ejecutan en servicios de infraestructura de Azure.</span><span class="sxs-lookup"><span data-stu-id="1612d-138">A simulated intranet running in Azure infrastructure services.</span></span>
    
- <span data-ttu-id="1612d-139">Suscripciones de prueba de Office 365 E5 Enterprise y EMS que comparten la misma organización y el mismo inquilino de AD Azure con la lista de cuentas de usuario.</span><span class="sxs-lookup"><span data-stu-id="1612d-139">Office 365 E5 Enterprise and EMS trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="1612d-140">Todas las cuentas de usuario habilitadas para usar Office 365 E5 Enterprise y EMS.</span><span class="sxs-lookup"><span data-stu-id="1612d-140">All of your user accounts enabled to use Office 365 E5 Enterprise and EMS.</span></span>
    
<span data-ttu-id="1612d-141">La figura 2 muestra la configuración resultante, que agrega EMS.</span><span class="sxs-lookup"><span data-stu-id="1612d-141">Figure 2 shows your resulting configuration, which adds EMS.</span></span>
  
<span data-ttu-id="1612d-142">**Figura 2: La intranet simulada en Azure con Office 365 y EMS**</span><span class="sxs-lookup"><span data-stu-id="1612d-142">**Figure 2: The simulated intranet in Azure with Office 365 and EMS**</span></span>

![Fase 2 del entorno de pruebas y desarrollo de One Microsoft Cloud con Azure, Office 365 y EMS](images/fdb520fe-ebbd-4681-a80e-b60df52f07c5.png)
  
## <a name="phase-3-add-dynamics-365"></a><span data-ttu-id="1612d-144">Fase 3: Agregar Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="1612d-144">Phase 3: Add Dynamics 365</span></span>

<span data-ttu-id="1612d-145">En esta fase, Inscríbase en la suscripción de prueba de Dynamics 365 y agregarlo a la misma organización que las suscripciones de prueba de Office 365 y EMS.</span><span class="sxs-lookup"><span data-stu-id="1612d-145">In this phase, you sign up for the Dynamics 365 trial subscription and add it to the same organization as your Office 365 and EMS trial subscriptions.</span></span>
  
1. <span data-ttu-id="1612d-146">Con un navegador desde ya sea el equipo de escritorio o desde CLIENTE1, iniciar sesión en el portal de Office 365 en [https://portal.office.com](https://portal.office.com) con las credenciales de la cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="1612d-146">Using a browser on either your desktop computer or from CLIENT1, sign in to the Office 365 portal at [https://portal.office.com](https://portal.office.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="1612d-147">Haga clic en el icono **Administración**.</span><span class="sxs-lookup"><span data-stu-id="1612d-147">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="1612d-148">En la ficha del **Centro de administración de Office** , en la exploración de la izquierda, haga clic en **de facturación > adquirir servicios**.</span><span class="sxs-lookup"><span data-stu-id="1612d-148">On the **Office admin center** tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="1612d-p105">En la página **Servicios de compra** , busque el elemento **Dynamics 365 Plan 1 Enterprise Edition** . Sitúe el puntero del mouse sobre él y haga clic en **iniciar la versión de prueba gratuita**.</span><span class="sxs-lookup"><span data-stu-id="1612d-p105">On the **Purchase services** page, find the **Dynamics 365 Plan 1 Enterprise Edition** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="1612d-151">En la página **Confirmar pedido**, haga clic en **Probar ahora**.</span><span class="sxs-lookup"><span data-stu-id="1612d-151">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="1612d-152">En la página **Recibo del pedido**, haga clic en **Continuar**.</span><span class="sxs-lookup"><span data-stu-id="1612d-152">On the **Order receipt** page, click **Continue**.</span></span>
    
> [!NOTE]
> <span data-ttu-id="1612d-p106">La suscripción de prueba de Dynamics 365 Plan 1 Enterprise Edition es de 30 días. Puede extender fácilmente la suscripción de prueba otros 30 días. Para un entorno de pruebas y desarrollo permanente, cree una nueva suscripción de pago con un número reducido de licencias.</span><span class="sxs-lookup"><span data-stu-id="1612d-p106">The Dynamics 365 Plan 1 Enterprise Edition trial subscription is 30 days. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
<span data-ttu-id="1612d-156">Utilice estos pasos para asignar licencias Dynamics 365 para el administrador global, 2 de usuario y cuentas de usuario 3 y hacer que los administradores del sistema.</span><span class="sxs-lookup"><span data-stu-id="1612d-156">Use these steps to assign Dynamics 365 licenses to the global administrator, User 2, and User 3 accounts and make them system administrators.</span></span>
  
1. <span data-ttu-id="1612d-157">En la ficha del **Centro de administración de Office** , haga clic en **los usuarios > usuarios activos**.</span><span class="sxs-lookup"><span data-stu-id="1612d-157">On the **Office admin center** tab, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="1612d-158">En la lista de usuarios activos, haga clic en la cuenta de administrador global y, a continuación, haga clic en **Editar** para **licencias de producto**.</span><span class="sxs-lookup"><span data-stu-id="1612d-158">In the list of active users, click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="1612d-159">En el panel de **licencias de producto** , activar la licencia del producto para **Dynamics 365 Plan 1 Enterprise Edition** **en**, haga clic en **Guardar** y, a continuación, haga clic en **Cerrar** dos veces.</span><span class="sxs-lookup"><span data-stu-id="1612d-159">On the **Product licenses** pane, turn the product license for **Dynamics 365 Plan 1 Enterprise Edition** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="1612d-160">Realice los pasos 2 y 3 para las cuentas Usuario 2 y Usuario 3.</span><span class="sxs-lookup"><span data-stu-id="1612d-160">Perform steps 2 and 3 for the User 2 and User 3 accounts.</span></span>
    
5. <span data-ttu-id="1612d-161">Cierre la ficha de **Centro de administración de Office** .</span><span class="sxs-lookup"><span data-stu-id="1612d-161">Close the **Office admin center** tab.</span></span>
    
<span data-ttu-id="1612d-162">Siga estos pasos para configurar las cuentas Usuario 2 y Usuario 3 como administradores del sistema de Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="1612d-162">Use these steps to configure the User 2 and User 3 accounts as Dynamics 365 system administrators.</span></span>
  
1. <span data-ttu-id="1612d-163">En la ficha del **Centro de administración de Office** en el explorador, en la exploración de la izquierda, haga clic en **centros de Admin**y, a continuación, haga clic en **Dynamics 365**.</span><span class="sxs-lookup"><span data-stu-id="1612d-163">On the **Office Admin center** tab in your browser, in the left navigation, click **Admin centers**, and then click **Dynamics 365**.</span></span>
    
    <span data-ttu-id="1612d-164">Es posible que deba esperar a que finalice el aprovisionamiento de Dynamics 365 para que este aparezca en el menú.</span><span class="sxs-lookup"><span data-stu-id="1612d-164">You may need to wait for Dynamics 365 to finish provisioning before Dynamics 365 appears in the menu.</span></span>
    
2. <span data-ttu-id="1612d-165">En la ficha de Dynamics 365, haga clic en **todos ellos**y, a continuación, haga clic en **Finalizar la instalación.**</span><span class="sxs-lookup"><span data-stu-id="1612d-165">On the Dynamics 365 tab, click **All of these**, and then click **Complete Setup.**</span></span>
    
    <span data-ttu-id="1612d-166">Espere a que se complete la configuración.</span><span class="sxs-lookup"><span data-stu-id="1612d-166">Wait for setup to complete.</span></span>
    
    <span data-ttu-id="1612d-p107">Cuando finalice la instalación, se muestra un panel de actividad de ventas basándose en datos de ejemplo que es parte de la suscripción de la pista. Tardar unos minutos para ver el **Bienvenido a la versión de prueba** de vídeo. Cierre la ventana de vídeo cuando haya terminado.</span><span class="sxs-lookup"><span data-stu-id="1612d-p107">When setup completes, it displays a Sales Activity Dashboard based on sample data that is part of the trail subscription. Take a few moments to view the **Welcome to your trial** video. Close the video window when complete.</span></span>
    
3. <span data-ttu-id="1612d-170">En la barra de herramientas en la parte superior, haga clic en la flecha abajo situada junto a la **venta**, haga clic en **configuración**y, a continuación, haga clic en **seguridad**.</span><span class="sxs-lookup"><span data-stu-id="1612d-170">On the toolbar at the top, click the down arrow next to **Sales**, click **Settings**, and then click **Security**.</span></span>
    
4. <span data-ttu-id="1612d-171">En la página **seguridad** , haga clic en **usuarios**.</span><span class="sxs-lookup"><span data-stu-id="1612d-171">On the **Security** page, click **Users**.</span></span>
    
5. <span data-ttu-id="1612d-172">En la lista de usuarios, haga clic en **usuario 2**.</span><span class="sxs-lookup"><span data-stu-id="1612d-172">In the list of users, click **User 2**.</span></span>
    
6. <span data-ttu-id="1612d-173">En la barra de herramientas, haga clic en **Administrar funciones**.</span><span class="sxs-lookup"><span data-stu-id="1612d-173">In the tool bar, click **Manage Roles**.</span></span>
    
7. <span data-ttu-id="1612d-174">En **Administrar Roles**, haga clic en **Administrador del sistema**y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="1612d-174">In **Manage Roles**, click **System Administrator**, and then click **OK**.</span></span>
    
8. <span data-ttu-id="1612d-175">En la barra de herramientas en la parte superior, haga clic en **seguridad**.</span><span class="sxs-lookup"><span data-stu-id="1612d-175">In the tool bar at the top click **Security**.</span></span>
    
9. <span data-ttu-id="1612d-176">Repita los pasos del 5 al 8 para la cuenta Usuario 3.</span><span class="sxs-lookup"><span data-stu-id="1612d-176">Repeat steps 5-8 for the User 3 account.</span></span>
    
10. <span data-ttu-id="1612d-177">Cerrar la **usuario: usuario3** ficha.</span><span class="sxs-lookup"><span data-stu-id="1612d-177">Close the **User: User3** tab.</span></span>
    
> [!NOTE]
> <span data-ttu-id="1612d-178">El rol de administrador del sistema de Dynamics 365 se asignó automáticamente a su cuenta de administrador global de Office 365.</span><span class="sxs-lookup"><span data-stu-id="1612d-178">Your Office 365 global administrator account was automatically assigned the Dynamics 365 system administrator role.</span></span> 
  
<span data-ttu-id="1612d-179">Ahora tiene su entorno de pruebas y desarrollo:</span><span class="sxs-lookup"><span data-stu-id="1612d-179">Your dev/test environment now has:</span></span>
  
- <span data-ttu-id="1612d-180">Intranet simulada que se ejecutan en servicios de infraestructura de Azure.</span><span class="sxs-lookup"><span data-stu-id="1612d-180">A simulated intranet running in Azure infrastructure services.</span></span>
    
- <span data-ttu-id="1612d-181">Office 365 E5 Enterprise, EMS y Dynamics 365 suscripciones de prueba compartiendo la misma organización y el mismo inquilino AD Azure con la lista de cuentas de usuario.</span><span class="sxs-lookup"><span data-stu-id="1612d-181">Office 365 E5 Enterprise, EMS, and Dynamics 365 trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="1612d-182">Todas las cuentas de usuario habilitadas para usar Office 365 E5 Enterprise y EMS.</span><span class="sxs-lookup"><span data-stu-id="1612d-182">All of your user accounts enabled to use Office 365 E5 Enterprise and EMS.</span></span>
    
- <span data-ttu-id="1612d-183">El administrador global de empresa, 2 de usuario y cuentas de usuario 3 están habilitadas para utilizar Dynamics 365 y son administradores del sistema Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="1612d-183">Your global enterprise administrator, User 2, and User 3 accounts are enabled to use Dynamics 365 and are Dynamics 365 system administrators.</span></span>
    
<span data-ttu-id="1612d-184">La figura 3 muestra la configuración resultante.</span><span class="sxs-lookup"><span data-stu-id="1612d-184">Figure 3 shows your resulting configuration.</span></span>
  
<span data-ttu-id="1612d-185">**Figura 3: La intranet simulada en Azure con Office 365, EMS y Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="1612d-185">**Figure 3: The simulated intranet in Azure with Office 365, EMS, and Dynamics 365**</span></span>

![Fase 3 del entorno de pruebas y desarrollo de One Microsoft Cloud con Azure, Office 365, EMS y Dynamics 365](images/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
## <a name="next-steps"></a><span data-ttu-id="1612d-187">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="1612d-187">Next steps</span></span>

<span data-ttu-id="1612d-p108">Ahora puede experimentar con el entorno de desarrollo y prueba de una nube de Microsoft. Aquí tiene algunas ideas para la experiencia guiada:</span><span class="sxs-lookup"><span data-stu-id="1612d-p108">You can now experiment with your One Microsoft Cloud dev/test environment. Here are some ideas for guided experiences:</span></span>
  
- [<span data-ttu-id="1612d-190">Configurar directivas de administración (MAM) de la aplicación móvil de EMS para aplicaciones de Office 365</span><span class="sxs-lookup"><span data-stu-id="1612d-190">Configure mobile application management (MAM) policies in EMS for Office 365 applications</span></span>](https://technet.microsoft.com/library/mt764059.aspx)
    
- [<span data-ttu-id="1612d-191">Demostrar Exchange Online en Office 365 integración con contactos de Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="1612d-191">Demonstrate Exchange Online in Office 365 integration with Dynamics 365 contacts</span></span>](https://technet.microsoft.com/library/mt798313.aspx)
    
- [<span data-ttu-id="1612d-192">Crear una red local entre simulado en servicios de infraestructura de Azure para alojar las cargas de trabajo basado en servidor</span><span class="sxs-lookup"><span data-stu-id="1612d-192">Create a simulated cross-premises network in Azure infrastructure services for hosting server-based workloads</span></span>](https://technet.microsoft.com/library/mt745150.aspx)
    
## <a name="see-also"></a><span data-ttu-id="1612d-193">Consulte también</span><span class="sxs-lookup"><span data-stu-id="1612d-193">See Also</span></span>

[<span data-ttu-id="1612d-194">Guías de entorno de pruebas de adopción de la nube (TLG)</span><span class="sxs-lookup"><span data-stu-id="1612d-194">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="1612d-195">Recursos de arquitectura de TI de la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="1612d-195">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="1612d-196">Soluciones híbridas</span><span class="sxs-lookup"><span data-stu-id="1612d-196">Hybrid solutions</span></span>](hybrid-solutions.md)
  
[<span data-ttu-id="1612d-197">Soluciones de seguridad</span><span class="sxs-lookup"><span data-stu-id="1612d-197">Security solutions</span></span>](security-solutions.md)





