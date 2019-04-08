---
title: El entorno de desarrollo y pruebas de One Microsoft Cloud
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: a1370fe4-2fd6-4fea-ad1d-3555433d6d2e
description: 'Resumen: use esta guía del entorno de pruebas para crear un entorno de desarrollo y pruebas donde se incluyan todas las ofertas de la nube de Microsoft.'
ms.openlocfilehash: b8ffd01c9d129d4537c82f0e1f74bd7c1be1388b
ms.sourcegitcommit: 201d3338d8bbc6da9389e62e2add8a17384fab4d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "31037954"
---
# <a name="the-one-microsoft-cloud-devtest-environment"></a><span data-ttu-id="67a67-103">El entorno de desarrollo y pruebas de One Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="67a67-103">The One Microsoft Cloud dev/test environment</span></span>

 <span data-ttu-id="67a67-104">**Resumen:** use esta guía del entorno de pruebas para crear un entorno de desarrollo y pruebas donde se incluyan todas las ofertas de la nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="67a67-104">**Summary:** Use this Test Lab Guide to create a dev/test environment that includes all of Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="67a67-p101">Con las instrucciones que aparecen en este artículo, creará una intranet simulada en los servicios de infraestructura de Microsoft Azure y, después, agregará suscripciones de Microsoft Office 365, Microsoft Enterprise Mobility + Security (EMS) y Microsoft Dynamics 365. El resultado es una organización simplificada que usa todas las ofertas de la nube de Microsoft al mismo tiempo en un único entorno de desarrollo y pruebas.</span><span class="sxs-lookup"><span data-stu-id="67a67-p101">With the instructions in this article, you create a simulated intranet in Microsoft Azure infrastructure services and then add Microsoft Office 365, Microsoft Enterprise Mobility + Security (EMS), and Microsoft Dynamics 365 subscriptions. The result is a simplified organization that uses all Microsoft's cloud offerings at the same time in a single dev/test environment.</span></span> 
  
![Fase 3 del entorno de desarrollo y pruebas de One Microsoft Cloud con Azure, Office 365, EMS y Dynamics 365](media/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
<span data-ttu-id="67a67-108">Puede usar la configuración resultante para:</span><span class="sxs-lookup"><span data-stu-id="67a67-108">You can use the resulting configuration to:</span></span>
  
- <span data-ttu-id="67a67-109">Probar la integración en las ofertas de la nube de Microsoft, como la infraestructura de identidades común proporcionada por Azure Active Directory (AD).</span><span class="sxs-lookup"><span data-stu-id="67a67-109">Experience the integration across Microsoft's cloud offerings, such as the common identity infrastructure provided by Azure Active Directory (AD).</span></span>
    
- <span data-ttu-id="67a67-110">Evaluar los escenarios integrales donde se incluyen varias ofertas de Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="67a67-110">Evaluate end-to-end scenarios that include multiple Microsoft Cloud offerings.</span></span>
    
- <span data-ttu-id="67a67-111">Crear una demostración, una prueba de concepto o una configuración de desarrollo y pruebas donde se usen varias ofertas de Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="67a67-111">Create a demo, proof-of-concept, or dev/test configuration that uses multiple Microsoft Cloud offerings.</span></span>
    
- <span data-ttu-id="67a67-112">Mejorar sus aptitudes de Microsoft Cloud para el desarrollo profesional.</span><span class="sxs-lookup"><span data-stu-id="67a67-112">Build your Microsoft Cloud skills for professional development.</span></span>
    
## <a name="phase-1-create-a-simulated-intranet-and-add-office-365"></a><span data-ttu-id="67a67-113">Fase 1: Crear una intranet simulada y agregar Office 365</span><span class="sxs-lookup"><span data-stu-id="67a67-113">Phase 1: Create a simulated intranet and add Office 365</span></span>

<span data-ttu-id="67a67-114">Siga las instrucciones que se indican en [DirSync para el entorno de desarrollo y pruebas de Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="67a67-114">Follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="67a67-115">En la ilustración 1, se muestra la configuración resultante, donde se incluye Office 365 y una intranet simulada que se ejecuta en los servicios de infraestructura de Azure y la sincronización de directorios desde un bosque local de Servicios de dominio de Active Directory (AD DS).</span><span class="sxs-lookup"><span data-stu-id="67a67-115">Figure 1 shows your resulting configuration, which includes Office 365 and a simulated intranet running in Azure infrastructure services and directory synchronization from an on-premises Windows Server Active Directory (AD) forest.</span></span>
  
<span data-ttu-id="67a67-116">**Ilustración 1: La intranet simulada en Azure con Office 365**</span><span class="sxs-lookup"><span data-stu-id="67a67-116">**Figure 1: The simulated intranet in Azure with Office 365**</span></span>

![El entorno de desarrollo y pruebas de Office 365 con DirSync](media/be5b37b0-f832-4878-b153-436c31546e21.png)
  
> [!NOTE]
> <span data-ttu-id="67a67-p102">La prueba de Azure dura 30 días. La suscripción de prueba de Office 365 Enterprise E5 dura 30 días y se puede ampliar fácilmente durante otros 30 días. Para obtener un entorno de desarrollo y pruebas permanente, cree una suscripción de Azure de pago y una suscripción de Office 365 Enterprise E5 con un número reducido de licencias.</span><span class="sxs-lookup"><span data-stu-id="67a67-p102">The Azure trial is 30 days. The Office 365 Enterprise E5 Trial subscription is 30 days, which can be easily extended for another 30 days. For a permanent dev/test environment, create a new paid Azure subscription and a new paid Office 365 Enterprise E5 subscription with a small number of licenses.</span></span> 
  
## <a name="phase-2-add-ems"></a><span data-ttu-id="67a67-121">Fase 2: Agregar EMS</span><span class="sxs-lookup"><span data-stu-id="67a67-121">Phase 2: Add EMS</span></span>

<span data-ttu-id="67a67-122">En esta fase, se inscribirá en la suscripción de prueba de EMS y la agregará a la misma organización que su suscripción de prueba de Office 365.</span><span class="sxs-lookup"><span data-stu-id="67a67-122">In this phase, you sign up for the EMS trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="67a67-123">Con un explorador con un equipo de escritorio o desde CLIENTE1, inicie sesión en el portal de Office 365 en [https://www.office.com](https://www.office.com) con las credenciales de la cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="67a67-123">With a browser on either your desktop computer or from CLIENT1, sign in to the Office 365 portal at [https://www.office.com](https://www.office.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="67a67-124">Haga clic en el icono **Administración**.</span><span class="sxs-lookup"><span data-stu-id="67a67-124">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="67a67-125">En la pestaña **Centro de administración de Office** del explorador, en el panel de navegación izquierdo, haga clic en **Facturación > Servicios de compra**.</span><span class="sxs-lookup"><span data-stu-id="67a67-125">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="67a67-p103">En la página **Servicios de compra**, busque el elemento **Enterprise Mobility + Security E5**. Mantenga el puntero del mouse sobre ese elemento y haga clic en **Iniciar prueba gratuita**.</span><span class="sxs-lookup"><span data-stu-id="67a67-p103">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="67a67-128">En la página **Confirmar pedido**, haga clic en **Probar ahora**.</span><span class="sxs-lookup"><span data-stu-id="67a67-128">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="67a67-129">En la página **Recibo del pedido**, haga clic en **Continuar**.</span><span class="sxs-lookup"><span data-stu-id="67a67-129">On the **Order receipt** page, click **Continue**.</span></span>
    
> [!NOTE]
> <span data-ttu-id="67a67-p104">La suscripción de prueba a Enterprise Mobility + Security E5 tiene una duración de 90 días. Si quiere usar un entorno de pruebas y desarrollo permanente, cree una nueva suscripción de pago con un número reducido de licencias.</span><span class="sxs-lookup"><span data-stu-id="67a67-p104">The Enterprise Mobility + Security E5 trial subscription is 90 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
<span data-ttu-id="67a67-132">Después, habilite la licencia de Enterprise Mobility + Security E5 para todas las cuentas de usuario.</span><span class="sxs-lookup"><span data-stu-id="67a67-132">Next, enable the Enterprise Mobility + Security E5 license for all user accounts.</span></span>
  
1. <span data-ttu-id="67a67-133">En la pestaña **Centro de administración de Office 365** del explorador, en el panel de navegación izquierdo, haga clic en **Usuarios > Usuarios activos**.</span><span class="sxs-lookup"><span data-stu-id="67a67-133">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="67a67-134">Haga clic en la cuenta de administrador global y, después, en **Editar** para **Licencias de productos**.</span><span class="sxs-lookup"><span data-stu-id="67a67-134">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="67a67-135">En el panel **Licencias de productos**, cambie la licencia del producto de **Enterprise Mobility + Security E5** a **Activada**, seleccione **Guardar** y, después, haga clic en **Cerrar** dos veces.</span><span class="sxs-lookup"><span data-stu-id="67a67-135">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="67a67-136">Para el resto de sus cuentas (Usuario 1, Usuario 2, Usuario 3, Usuario 4 y Usuario 5), complete los pasos 2 y 3.</span><span class="sxs-lookup"><span data-stu-id="67a67-136">For all of your other accounts (User1, User 2, User 3, User 4, and User 5), do steps 2 and 3.</span></span>
    
<span data-ttu-id="67a67-137">Ahora, su entorno de desarrollo y pruebas tiene:</span><span class="sxs-lookup"><span data-stu-id="67a67-137">Your dev/test environment now has:</span></span>
  
- <span data-ttu-id="67a67-138">Una intranet simulada donde se ejecutan servicios de infraestructura de Azure.</span><span class="sxs-lookup"><span data-stu-id="67a67-138">A simulated intranet running in Azure infrastructure services.</span></span>
    
- <span data-ttu-id="67a67-139">Suscripciones de prueba de Office 365 E5 Enterprise y EMS que comparten la misma organización y el mismo inquilino de AD Azure con la lista de cuentas de usuario.</span><span class="sxs-lookup"><span data-stu-id="67a67-139">Office 365 E5 Enterprise and EMS trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="67a67-140">Todas las cuentas de usuario habilitadas para usar Office 365 Enterprise E5 y EMS.</span><span class="sxs-lookup"><span data-stu-id="67a67-140">All of your user accounts enabled to use Office 365 E5 Enterprise and EMS.</span></span>
    
<span data-ttu-id="67a67-141">En la ilustración 2, se muestra la configuración resultante, que agrega EMS.</span><span class="sxs-lookup"><span data-stu-id="67a67-141">Figure 2 shows your resulting configuration, which adds EMS.</span></span>
  
<span data-ttu-id="67a67-142">**Ilustración 2: La intranet simulada en Azure con Office 365 y EMS**</span><span class="sxs-lookup"><span data-stu-id="67a67-142">**Figure 2: The simulated intranet in Azure with Office 365 and EMS**</span></span>

![Fase 2 del entorno de desarrollo y pruebas de One Microsoft Cloud con Azure, Office 365 y EMS](media/fdb520fe-ebbd-4681-a80e-b60df52f07c5.png)
  
## <a name="phase-3-add-dynamics-365"></a><span data-ttu-id="67a67-144">Fase 3: Agregar Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="67a67-144">Phase 3: Add Dynamics 365</span></span>

<span data-ttu-id="67a67-145">En esta fase, se registrará en la suscripción de prueba a Dynamics 365 y la agregará a la misma organización que su suscripción de prueba a Office 365 y EMS.</span><span class="sxs-lookup"><span data-stu-id="67a67-145">In this phase, you sign up for the Dynamics 365 trial subscription and add it to the same organization as your Office 365 and EMS trial subscriptions.</span></span>
  
1. <span data-ttu-id="67a67-146">Con un explorador con un equipo de escritorio o desde CLIENTE1, inicie sesión en el portal de Office 365 en [https://www.office.com](https://www.office.com) con las credenciales de la cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="67a67-146">Using a browser on either your desktop computer or from CLIENT1, sign in to the Office 365 portal at [https://www.office.com](https://www.office.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="67a67-147">Haga clic en el icono **Administrador**.</span><span class="sxs-lookup"><span data-stu-id="67a67-147">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="67a67-148">En la pestaña **Centro de administración de Microsoft 365**, en el panel de navegación izquierdo, haga clic en **Facturación > Servicios de compra**.</span><span class="sxs-lookup"><span data-stu-id="67a67-148">On the **Microsoft 365 admin center** tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="67a67-p105">En la página **Servicios de compra**, busque el elemento **Dynamics 365 (plan 1) Enterprise Edition**. Mantenga el puntero del mouse sobre ese elemento y haga clic en **Iniciar prueba gratuita**.</span><span class="sxs-lookup"><span data-stu-id="67a67-p105">On the **Purchase services** page, find the **Dynamics 365 Plan 1 Enterprise Edition** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="67a67-151">En la página **Confirmar pedido**, haga clic en **Probar ahora**.</span><span class="sxs-lookup"><span data-stu-id="67a67-151">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="67a67-152">En la página **Recibo del pedido**, haga clic en **Continuar**.</span><span class="sxs-lookup"><span data-stu-id="67a67-152">On the **Order receipt** page, click **Continue**.</span></span>
    
> [!NOTE]
> <span data-ttu-id="67a67-p106">La suscripción de prueba de Dynamics 365 Plan 1 Enterprise Edition es de 30 días. Puede extender fácilmente la suscripción de prueba otros 30 días. Para un entorno de pruebas y desarrollo permanente, cree una nueva suscripción de pago con un número reducido de licencias.</span><span class="sxs-lookup"><span data-stu-id="67a67-p106">The Dynamics 365 Plan 1 Enterprise Edition trial subscription is 30 days. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
<span data-ttu-id="67a67-156">Siga este procedimiento para asignar las licencias de Dynamics 365 al administrador global y a las cuentas Usuario 2 y Usuario 3, y los hará administradores del sistema.</span><span class="sxs-lookup"><span data-stu-id="67a67-156">Use these steps to assign Dynamics 365 licenses to the global administrator, User 2, and User 3 accounts and make them system administrators.</span></span>
  
1. <span data-ttu-id="67a67-157">En la pestaña **Centro de administración de Microsoft 365**, haga clic en **Usuarios > Usuarios activos**.</span><span class="sxs-lookup"><span data-stu-id="67a67-157">On the **Microsoft 365 admin center** tab, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="67a67-158">En la lista de usuarios activos, haga clic en su cuenta de administrador global y, después, haga clic en **Editar** en **Licencias de productos**.</span><span class="sxs-lookup"><span data-stu-id="67a67-158">In the list of active users, click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="67a67-159">	En el panel *\*Licencias de productos*\*, cambie la licencia del producto de *\*Dynamics 365 (plan 1) Enterprise Edition** a *\*Activada*\*, seleccione *\*Guardar** y, después, haga clic en *\*Cerrar** dos veces.</span><span class="sxs-lookup"><span data-stu-id="67a67-159">On the **Product licenses** pane, turn the product license for **Dynamics 365 Plan 1 Enterprise Edition** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="67a67-160">Realice los pasos 2 y 3 para las cuentas Usuario 2 y Usuario 3.</span><span class="sxs-lookup"><span data-stu-id="67a67-160">Perform steps 2 and 3 for the User 2 and User 3 accounts.</span></span>
    
5. <span data-ttu-id="67a67-161">Cierre la pestaña del **Centro de administración de Microsoft 365**.</span><span class="sxs-lookup"><span data-stu-id="67a67-161">Close the **Microsoft 365 admin center** tab.</span></span>
    
<span data-ttu-id="67a67-162">Siga estos pasos para configurar las cuentas Usuario 2 y Usuario 3 como administradores del sistema de Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="67a67-162">Use these steps to configure the User 2 and User 3 accounts as Dynamics 365 system administrators.</span></span>
  
1. <span data-ttu-id="67a67-163">En la pestaña **Centro de administración de Office** en el explorador, en el panel de navegación izquierdo, haga clic en **Centros de administración** y, después, seleccione **Dynamics 365**.</span><span class="sxs-lookup"><span data-stu-id="67a67-163">On the **Office Admin center** tab in your browser, in the left navigation, click **Admin centers**, and then click **Dynamics 365**.</span></span>
    
    <span data-ttu-id="67a67-164">Es posible que tenga que esperar hasta que finalice el aprovisionamiento de Dynamics 365 para que este aparezca en el menú.</span><span class="sxs-lookup"><span data-stu-id="67a67-164">You may need to wait for Dynamics 365 to finish provisioning before Dynamics 365 appears in the menu.</span></span>
    
2. <span data-ttu-id="67a67-165">En la pestaña Dynamics 365, haga clic en **Todos estos** y, después, en **Finalizar configuración**.</span><span class="sxs-lookup"><span data-stu-id="67a67-165">On the Dynamics 365 tab, click **All of these**, and then click **Complete Setup.**</span></span>
    
    <span data-ttu-id="67a67-166">Espere a que se complete la configuración.</span><span class="sxs-lookup"><span data-stu-id="67a67-166">Wait for setup to complete.</span></span>
    
    <span data-ttu-id="67a67-p107">Cuando se complete la configuración, se mostrará un Panel de actividad de ventas basado en datos de ejemplo que forman parte de la suscripción de prueba. Dedique unos minutos a ver el vídeo **Bienvenido a la prueba**. Cuando termine, cierre la ventana del vídeo.</span><span class="sxs-lookup"><span data-stu-id="67a67-p107">When setup completes, it shows a Sales Activity Dashboard based on sample data that is part of the trail subscription. Take a few moments to view the **Welcome to your trial** video. Close the video window when complete.</span></span>
    
3. <span data-ttu-id="67a67-170">En la barra de herramientas de la parte superior, haga clic en la flecha abajo junto a **Ventas**, seleccione **Configuración** y, después, haga clic en **Seguridad**.</span><span class="sxs-lookup"><span data-stu-id="67a67-170">On the toolbar at the top, click the down arrow next to **Sales**, click **Settings**, and then click **Security**.</span></span>
    
4. <span data-ttu-id="67a67-171">En la página **Seguridad**, haga clic en **Usuarios**.</span><span class="sxs-lookup"><span data-stu-id="67a67-171">On the **Security** page, click **Users**.</span></span>
    
5. <span data-ttu-id="67a67-172">En la lista de usuarios, haga clic en **Usuario 2**.</span><span class="sxs-lookup"><span data-stu-id="67a67-172">In the list of users, click **User 2**.</span></span>
    
6. <span data-ttu-id="67a67-173">En la barra de herramientas, haga clic en **Administrar roles**.</span><span class="sxs-lookup"><span data-stu-id="67a67-173">In the tool bar, click **Manage Roles**.</span></span>
    
7. <span data-ttu-id="67a67-174">En **Administrar roles**, haga clic en **Administrador del sistema** y, después, en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="67a67-174">In **Manage Roles**, click **System Administrator**, and then click **OK**.</span></span>
    
8. <span data-ttu-id="67a67-175">En la barra de herramientas de la parte superior, haga clic en **Seguridad**.</span><span class="sxs-lookup"><span data-stu-id="67a67-175">In the tool bar at the top click **Security**.</span></span>
    
9. <span data-ttu-id="67a67-176">Repita los pasos del 5 al 8 para la cuenta Usuario 3.</span><span class="sxs-lookup"><span data-stu-id="67a67-176">Repeat steps 5-8 for the User 3 account.</span></span>
    
10. <span data-ttu-id="67a67-177">Cierre la pestaña **Usuario: Usuario3**.</span><span class="sxs-lookup"><span data-stu-id="67a67-177">Close the **User: User3** tab.</span></span>
    
> [!NOTE]
> <span data-ttu-id="67a67-178">El rol de administrador del sistema de Dynamics 365 se asignó automáticamente a su cuenta de administrador global de Office 365.</span><span class="sxs-lookup"><span data-stu-id="67a67-178">Your Office 365 global administrator account was automatically assigned the Dynamics 365 system administrator role.</span></span> 
  
<span data-ttu-id="67a67-179">Ahora, su entorno de desarrollo y pruebas tiene:</span><span class="sxs-lookup"><span data-stu-id="67a67-179">Your dev/test environment now has:</span></span>
  
- <span data-ttu-id="67a67-180">Una intranet simulada donde se ejecutan servicios de infraestructura de Azure.</span><span class="sxs-lookup"><span data-stu-id="67a67-180">A simulated intranet running in Azure infrastructure services.</span></span>
    
- <span data-ttu-id="67a67-181">Suscripciones de prueba de Office 365 Enterprise E5, EMS y Dynamics 365 que comparten la misma organización y el mismo espacio empresarial de Azure AD con su lista de cuentas de usuario.</span><span class="sxs-lookup"><span data-stu-id="67a67-181">Office 365 E5 Enterprise, EMS, and Dynamics 365 trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="67a67-182">Todas las cuentas de usuario habilitadas para usar Office 365 Enterprise E5 y EMS.</span><span class="sxs-lookup"><span data-stu-id="67a67-182">All of your user accounts enabled to use Office 365 E5 Enterprise and EMS.</span></span>
    
- <span data-ttu-id="67a67-183">Sus cuentas de administrador de la organización global, Usuario 2 y Usuario 3 están habilitadas para usar Dynamics 365 y son administradores del sistema de Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="67a67-183">Your global enterprise administrator, User 2, and User 3 accounts are enabled to use Dynamics 365 and are Dynamics 365 system administrators.</span></span>
    
<span data-ttu-id="67a67-184">En la ilustración 3, se muestra la configuración resultante.</span><span class="sxs-lookup"><span data-stu-id="67a67-184">Figure 3 shows your resulting configuration.</span></span>
  
<span data-ttu-id="67a67-185">**Ilustración 3: La intranet simulada en Azure con Office 365, EMS y Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="67a67-185">**Figure 3: The simulated intranet in Azure with Office 365, EMS, and Dynamics 365**</span></span>

![Fase 3 del entorno de desarrollo y pruebas de One Microsoft Cloud con Azure, Office 365, EMS y Dynamics 365](media/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
## <a name="next-steps"></a><span data-ttu-id="67a67-187">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="67a67-187">Next steps</span></span>

<span data-ttu-id="67a67-p108">Ahora puede experimentar con el entorno de desarrollo y pruebas de One Microsoft Cloud. Aquí contra algunas ideas para experiencias guiadas:</span><span class="sxs-lookup"><span data-stu-id="67a67-p108">You can now experiment with your One Microsoft Cloud dev/test environment. Here are some ideas for guided experiences:</span></span>
  
- [<span data-ttu-id="67a67-190">Configurar directivas de administración de aplicaciones móviles (MAM) en EMS para aplicaciones de Office 365</span><span class="sxs-lookup"><span data-stu-id="67a67-190">Configure mobile application management (MAM) policies in EMS for Office 365 applications</span></span>](https://technet.microsoft.com/library/mt764059.aspx)
    
- [<span data-ttu-id="67a67-191">Demostrar Exchange Online en la integración de Office 365 con contactos de Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="67a67-191">Demonstrate Exchange Online in Office 365 integration with Dynamics 365 contacts</span></span>](https://technet.microsoft.com/library/mt798313.aspx)
    
- [<span data-ttu-id="67a67-192">Crear una red entre locales simulada en los servicios de infraestructura de Azure para hospedar cargas de trabajo basadas en servidor</span><span class="sxs-lookup"><span data-stu-id="67a67-192">Create a simulated cross-premises network in Azure infrastructure services for hosting server-based workloads</span></span>](https://technet.microsoft.com/library/mt745150.aspx)
    
## <a name="see-also"></a><span data-ttu-id="67a67-193">Vea también</span><span class="sxs-lookup"><span data-stu-id="67a67-193">See Also</span></span>

[<span data-ttu-id="67a67-194">Guías del entorno de pruebas de adopción de la nube (TLG)</span><span class="sxs-lookup"><span data-stu-id="67a67-194">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="67a67-195">Recursos de arquitectura de TI de Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="67a67-195">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="67a67-196">Soluciones híbridas</span><span class="sxs-lookup"><span data-stu-id="67a67-196">Hybrid solutions</span></span>](hybrid-solutions.md)
  
[<span data-ttu-id="67a67-197">Soluciones de seguridad</span><span class="sxs-lookup"><span data-stu-id="67a67-197">Security solutions</span></span>](security-solutions.md)





