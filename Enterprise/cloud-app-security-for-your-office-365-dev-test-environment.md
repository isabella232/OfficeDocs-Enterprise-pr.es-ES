---
title: Cloud App Security para el entorno de desarrollo y pruebas de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/05/2018
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 22248f2f-b370-435e-b6ac-0ae0cae36b96
description: 'Resumen: Configure y demuestre Office 365 Cloud App Security en su entorno de desarrollo y pruebas de Office 365.'
ms.openlocfilehash: af2a2657ede46818b9d705ca38f99d779f98fb11
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068106"
---
# <a name="cloud-app-security-for-your-office-365-devtest-environment"></a><span data-ttu-id="a1857-103">Cloud App Security para el entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="a1857-103">Cloud App Security for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="a1857-104">**Resumen:** Configure y demuestre Office 365 Cloud App Security en su entorno de desarrollo y pruebas de Office 365.</span><span class="sxs-lookup"><span data-stu-id="a1857-104">**Summary:** Configure and demonstrate Office 365 Cloud App Security in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="a1857-105">Office 365 Cloud App Security, anteriormente conocido como Office 365 Advanced Security Management, le permite crear directivas que supervisan e informan de actividades sospechosas en su suscripción a Office 365, de modo que pueda investigar y realizar posibles correcciones acciona.</span><span class="sxs-lookup"><span data-stu-id="a1857-105">Office 365 Cloud App Security, previously known as Office 365 Advanced Security Management, lets you create policies that monitor for and inform you of suspicious activities in your Office 365 subscription, so that you can investigate and take possible remediation action.</span></span> <span data-ttu-id="a1857-106">Para obtener más información, vea [información general sobre Cloud App Security en Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).</span><span class="sxs-lookup"><span data-stu-id="a1857-106">For more information, see [Overview of Cloud App Security in Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).</span></span>
  
<span data-ttu-id="a1857-107">Con las instrucciones de este artículo, puede habilitar y probar Cloud App Security en su suscripción de prueba de Office 365.</span><span class="sxs-lookup"><span data-stu-id="a1857-107">With the instructions in this article, you enable and test Cloud App Security in your Office 365 trial subscription.</span></span>
  
> [!TIP]
> <span data-ttu-id="a1857-108">Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual de todos los artículos en la pila de la Guía del entorno de pruebas de Office 365.</span><span class="sxs-lookup"><span data-stu-id="a1857-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="a1857-109">Fase 1: Crear un entorno de desarrollo y pruebas ligero o de una empresa simulada de Office 365</span><span class="sxs-lookup"><span data-stu-id="a1857-109">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="a1857-110">Si solo quiere probar Cloud App Security de manera ligera con los requisitos mínimos, siga las instrucciones indicadas en las fases 2 y 3 del [entorno de desarrollo y pruebas de Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="a1857-110">If you just want to test Cloud App Security in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="a1857-111">Si quiere probar Cloud App Security en una empresa simulada, siga las instrucciones que se indican en [DirSync para el entorno de desarrollo y pruebas de Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="a1857-111">If you want to test Cloud App Security in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="a1857-112">La prueba de Cloud App Security no requiere el entorno de desarrollo y pruebas de una empresa simulada, que incluye una intranet simulada conectada a Internet y la sincronización de directorios para un bosque de servicios de dominio de Active Directory (AD DS).</span><span class="sxs-lookup"><span data-stu-id="a1857-112">Testing Cloud App Security does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for an Active Directory Domain Services (AD DS) forest.</span></span> <span data-ttu-id="a1857-113">Se proporciona aquí como una opción para poder probar Cloud App Security y experimentar con ella en un entorno que representa una organización típica.</span><span class="sxs-lookup"><span data-stu-id="a1857-113">It is provided here as an option so that you can test Cloud App Security and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-before-enabling-cloud-app-security-and-creating-a-policy"></a><span data-ttu-id="a1857-114">Fase 2: antes de habilitar Cloud App Security y crear una directiva</span><span class="sxs-lookup"><span data-stu-id="a1857-114">Phase 2: Before enabling Cloud App Security and creating a policy</span></span>

<span data-ttu-id="a1857-115">En este procedimiento, se demuestra que antes de habilitar Cloud App Security, cambiar el rol de un usuario no proporciona ninguna notificación de correo electrónico al administrador global.</span><span class="sxs-lookup"><span data-stu-id="a1857-115">In this procedure, you demonstrate that before enabling Cloud App Security, changing a user's role provides no email notification to the global administrator.</span></span>
  
### <a name="test-the-default-notification-behavior-of-office-365"></a><span data-ttu-id="a1857-116">Probar el comportamiento de notificación predeterminado de Office 365</span><span class="sxs-lookup"><span data-stu-id="a1857-116">Test the default notification behavior of Office 365</span></span>

1. <span data-ttu-id="a1857-117">Vaya al centro de administración de 365 de[https://admin.microsoft.com](https://admin.microsoft.com)Microsoft () e inicie sesión en su suscripción de prueba de Office 365 con su cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="a1857-117">Go to the Microsoft 365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
  - <span data-ttu-id="a1857-118">Si usa el entorno de desarrollo y pruebas ligero de Office 365, inicie sesión desde el equipo local.</span><span class="sxs-lookup"><span data-stu-id="a1857-118">If you are using the lightweight Office 365 dev/test environment, sign in from your local computer.</span></span>
    
  - <span data-ttu-id="a1857-119">Si usa el entorno de desarrollo y pruebas de una empresa simulada de Office 365, use [Azure portal](https://portal.azure.com) para conectarse a la máquina virtual CLIENT1 y, a continuación, inicie sesión desde cliente1.</span><span class="sxs-lookup"><span data-stu-id="a1857-119">If you are using the simulated enterprise Office 365 dev/test environment, use the [Azure portal](https://portal.azure.com) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="a1857-120">En la página principal del portal, haga clic en **Administración**.</span><span class="sxs-lookup"><span data-stu-id="a1857-120">From the main portal page, click **Admin**.</span></span>
    
3. <span data-ttu-id="a1857-121">En el panel de navegación izquierdo, haga clic en **Usuarios > Usuarios activos**.</span><span class="sxs-lookup"><span data-stu-id="a1857-121">In the left navigation, click **Users > Active users**.</span></span>
    
4. <span data-ttu-id="a1857-122">	Haga clic en la cuenta *\*Usuario 4*\*.</span><span class="sxs-lookup"><span data-stu-id="a1857-122">Click the **User 4** account.</span></span>
    
5. <span data-ttu-id="a1857-123">En la página del **Usuario 4**, haga clic en **Editar** en la fila **Roles**.</span><span class="sxs-lookup"><span data-stu-id="a1857-123">On the **User 4** page, click **Edit** for the **Roles** row.</span></span>
    
6. <span data-ttu-id="a1857-p103">En la página **Edit user roles** (Editar roles de usuario), haga clic en **Administrador global**, escriba **user4@contoso.com** en **Alternative email address** (Dirección de correo electrónico alternativa) y haga clic en **Guardar**. Haga clic dos veces en **Cerrar**.</span><span class="sxs-lookup"><span data-stu-id="a1857-p103">On the **Edit user roles** page, click **Global administrator**, type **user4@contoso.com** in the **Alternative email address**, and then click **Save**. Click **Close** twice.</span></span>
    
7. <span data-ttu-id="a1857-126">	Seleccione el icono del iniciador de aplicaciones en la esquina superior izquierda y elija *\*Correo*\*.</span><span class="sxs-lookup"><span data-stu-id="a1857-126">Select the app launcher icon in the upper-left and choose **Mail**.</span></span>
    
8. <span data-ttu-id="a1857-127">Espere 30 minutos.</span><span class="sxs-lookup"><span data-stu-id="a1857-127">Wait 30 minutes.</span></span> <span data-ttu-id="a1857-128">Observe que no hay ningún mensaje de correo electrónico en la bandeja de entrada que le notifique el cambio en el rol del usuario 4 como administrador global.</span><span class="sxs-lookup"><span data-stu-id="a1857-128">Notice that there is no email message in the inbox notifying you of the change in User 4's role as a global administrator.</span></span>
    
## <a name="phase-3-enable-cloud-app-security-and-create-a-policy"></a><span data-ttu-id="a1857-129">Fase 3: habilitar Cloud App Security y crear una directiva</span><span class="sxs-lookup"><span data-stu-id="a1857-129">Phase 3: Enable Cloud App Security and create a policy</span></span>

<span data-ttu-id="a1857-130">En este procedimiento, se habilita Cloud App Security y se crea una nueva Directiva para enviar notificaciones de correo electrónico a la cuenta de administrador global para los cambios en los roles de cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="a1857-130">In this procedure, you enable Cloud App Security and create a new policy to send email notifications to your global administrator account for changes in user account roles.</span></span> <span data-ttu-id="a1857-131">Este procedimiento requiere lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="a1857-131">This procedure requires:</span></span>
  
- <span data-ttu-id="a1857-132">El nombre y la contraseña de la cuenta de administrador global de la suscripción de prueba de Office 365.</span><span class="sxs-lookup"><span data-stu-id="a1857-132">The global administrator account name and password of your Office 365 trial subscription.</span></span>
    
- <span data-ttu-id="a1857-133">El nombre y la contraseña de la cuenta del Usuario 5 de la suscripción de prueba de Office 365.</span><span class="sxs-lookup"><span data-stu-id="a1857-133">The name and password of the User 5 account of your Office 365 trial subscription.</span></span>
    
### <a name="enable-and-configure-cloud-app-security"></a><span data-ttu-id="a1857-134">Habilitar y configurar Cloud App Security</span><span class="sxs-lookup"><span data-stu-id="a1857-134">Enable and configure Cloud App Security</span></span>

1. <span data-ttu-id="a1857-135">Vaya al centro de administración de 365 de[https://admin.microsoft.com](https://admin.microsoft.com)Microsoft () e inicie sesión en su suscripción de prueba de Office 365 con su cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="a1857-135">Go to the Microsoft 365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="a1857-136">Haga clic en el icono **Administración**.</span><span class="sxs-lookup"><span data-stu-id="a1857-136">Click the **Admin** tile.</span></span> <span data-ttu-id="a1857-137">En la pestaña **centro de administración de Office** , haga clic en centros de **Administración _GT_ seguridad de & cumplimiento**.</span><span class="sxs-lookup"><span data-stu-id="a1857-137">On the **Office Admin center** tab, click **Admin centers > Security & Compliance**.</span></span>
    
3. <span data-ttu-id="a1857-138">En el panel de navegación izquierdo, haga clic en **alertas > de administración de alertas avanzadas**.</span><span class="sxs-lookup"><span data-stu-id="a1857-138">In the left navigation pane, click **Alerts > Manage advanced alerts**.</span></span>
    
4. <span data-ttu-id="a1857-139">En la página **Administrar alertas avanzadas** , haga clic en **activar Office 365 Cloud App Security**y, a continuación, haga clic en **ir a Office 365 Cloud App Security**.</span><span class="sxs-lookup"><span data-stu-id="a1857-139">On the **Manage advanced alerts** page, click **Turn on Office 365 Cloud App Security**, and then click **Go to Office 365 Cloud App Security**.</span></span>
    
5. <span data-ttu-id="a1857-140">En la pestaña nuevo **Panel** , haga clic en **directivas de > de control**.</span><span class="sxs-lookup"><span data-stu-id="a1857-140">On the new **Dashboard** tab, click **Control > Policies**.</span></span>
    
6. <span data-ttu-id="a1857-141">En la página **Directiva** , haga clic en **crear Directiva**y, a continuación, haga clic en **Directiva de actividad**.</span><span class="sxs-lookup"><span data-stu-id="a1857-141">On the **Policy** page, click **Create policy**, and then click **Activity policy**.</span></span>
    
7. <span data-ttu-id="a1857-142">En **nombre**de la Directiva, escriba **actividad administrativa**.</span><span class="sxs-lookup"><span data-stu-id="a1857-142">In **Policy name**, type **Administrative activity**.</span></span>
    
8. <span data-ttu-id="a1857-143">En **Gravedad de directiva**, haga clic en **Alto**.</span><span class="sxs-lookup"><span data-stu-id="a1857-143">In **Policy severity**, click **High**.</span></span>
    
9. <span data-ttu-id="a1857-144">En **categoría**, haga clic en **cuentas con privilegios**.</span><span class="sxs-lookup"><span data-stu-id="a1857-144">In **Category**, click **Privileged accounts**.</span></span>
    
10. <span data-ttu-id="a1857-145">En **crear filtros para la Directiva**, en **actividades que coincidan con todas las opciones siguientes**, haga clic en **actividad administrativa**.</span><span class="sxs-lookup"><span data-stu-id="a1857-145">In **Create filters for the policy**, in **Activities matching all of the following**, click **Administrative activity**.</span></span>
    
11. <span data-ttu-id="a1857-p107">En **Alertas**, haga clic en **Enviar alerta como mensaje de correo electrónico**. En **Para**, escriba la dirección de correo electrónico de la cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="a1857-p107">In **Alerts**, click **Send alert as email**. In **To**, type the email address of your global administrator account.</span></span>
    
12. <span data-ttu-id="a1857-148">En la parte inferior de la página, haga clic en **Crear**.</span><span class="sxs-lookup"><span data-stu-id="a1857-148">At the bottom of the page, click **Create**.</span></span>
    
## <a name="phase-4-show-cloud-app-security-in-action"></a><span data-ttu-id="a1857-149">Fase 4: Mostrar Cloud App Security en acción</span><span class="sxs-lookup"><span data-stu-id="a1857-149">Phase 4: Show Cloud App Security in action</span></span>

<span data-ttu-id="a1857-150">En este procedimiento, demostrará cómo Cloud App Security crea alertas y envía notificaciones de correo electrónico a la cuenta de administrador global cuando el usuario 4 convierte al usuario 5 en una contraseña y un administrador de administración de usuarios.</span><span class="sxs-lookup"><span data-stu-id="a1857-150">In this procedure, you demonstrate how Cloud App Security creates alerts and sends email notifications to the global administrator account when User 4 makes User 5 a password and user management administrator.</span></span>
  
### <a name="demonstrate-email-notification-for-a-change-in-user-account-roles"></a><span data-ttu-id="a1857-151">Demostración de la notificación por correo electrónico en caso de cambio en los roles de la cuenta de usuario</span><span class="sxs-lookup"><span data-stu-id="a1857-151">Demonstrate email notification for a change in user account roles</span></span>

1. <span data-ttu-id="a1857-152">En la esquina superior derecha, haga clic en el icono de usuario y después en **Cerrar sesión**.</span><span class="sxs-lookup"><span data-stu-id="a1857-152">In the upper-right, click the user icon, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="a1857-153">Vaya a [https://www.office.com](https://www.office.com).</span><span class="sxs-lookup"><span data-stu-id="a1857-153">Go to [https://www.office.com](https://www.office.com).</span></span>
    
3. <span data-ttu-id="a1857-154">En la página de inicio de sesión de Office 365, haga clic en **Usar otra cuenta**.</span><span class="sxs-lookup"><span data-stu-id="a1857-154">On the Office 365 sign in page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="a1857-155">Escriba el nombre de cuenta del Usuario 4 y su contraseña y luego haga clic en **Iniciar sesión**.</span><span class="sxs-lookup"><span data-stu-id="a1857-155">Type the User 4 account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="a1857-156">Si es necesario, cambie la contraseña de la cuenta del Usuario 4 y después haga clic en **Actualizar contraseña e iniciar sesión**.</span><span class="sxs-lookup"><span data-stu-id="a1857-156">If needed, change the User 4 account password, and then click **Update password and sign in**.</span></span>
    
6. <span data-ttu-id="a1857-157">En la página del Portal de Office 365, haga clic en **Administración**.</span><span class="sxs-lookup"><span data-stu-id="a1857-157">On the Office 365 portal page, click **Admin**.</span></span>
    
7. <span data-ttu-id="a1857-158">Si es necesario, haga clic en **Cancelar** cuando se le pida que actualice su información de contacto de administrador.</span><span class="sxs-lookup"><span data-stu-id="a1857-158">If needed, click **cancel** when prompted to update your admin contact info.</span></span>
    
8. <span data-ttu-id="a1857-159">En la página principal del portal, haga clic en **Administración**.</span><span class="sxs-lookup"><span data-stu-id="a1857-159">From the main portal page, click **Admin**.</span></span>
    
9. <span data-ttu-id="a1857-160">En el panel de navegación izquierdo, haga clic en **Usuarios > Usuarios activos**.</span><span class="sxs-lookup"><span data-stu-id="a1857-160">In the left navigation, click **Users > Active users**.</span></span>
    
10. <span data-ttu-id="a1857-161">Haga clic en la cuenta **Usuario 5**.</span><span class="sxs-lookup"><span data-stu-id="a1857-161">Click the **User 5** account.</span></span>
    
11. <span data-ttu-id="a1857-162">En la página del **Usuario 5**, haga clic en **Editar** en la fila **Roles**.</span><span class="sxs-lookup"><span data-stu-id="a1857-162">On the **User 5** page, click **Edit** for the **Roles** row.</span></span>
    
12. <span data-ttu-id="a1857-p108">En la página **Edit user roles** (Editar roles de usuario), haga clic en **Customized administrator** (Administrador personalizado), haga clic en **Administrador de contraseñas** y **Administrador de control de usuarios**, escriba **user5@contoso.com** en **Alternative email address** (Dirección de correo electrónico alternativa) y haga clic en **Guardar**. Haga clic dos veces en **Cerrar**.</span><span class="sxs-lookup"><span data-stu-id="a1857-p108">On the **Edit user roles** page, click **Customized administrator**, click **Password administrator** and **User management administrator**, type **user5@contoso.com** in the **Alternative email address**, and then click **Save**. Click **Close** twice.</span></span>
    
13. <span data-ttu-id="a1857-165">Haga clic en el icono de usuario en la esquina superior derecha y después en **Cerrar sesión**.</span><span class="sxs-lookup"><span data-stu-id="a1857-165">Click the user icon in the upper-right, and then click **Sign out**.</span></span> 
    
14. <span data-ttu-id="a1857-166">Vaya a [https://www.office.com](https://www.office.com).</span><span class="sxs-lookup"><span data-stu-id="a1857-166">Go to [https://www.office.com](https://www.office.com).</span></span>
    
15. <span data-ttu-id="a1857-167">En la página **Inicio de sesión en Office 365**, haga clic en el nombre de la cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="a1857-167">On the **Office 365 sign in** page, click your global administrator account name.</span></span>
    
16. <span data-ttu-id="a1857-168">Escriba la contraseña y haga clic en **Iniciar sesión**.</span><span class="sxs-lookup"><span data-stu-id="a1857-168">Type the password, and then click **Sign in**.</span></span>
    
17. <span data-ttu-id="a1857-169">En la página del portal de Office 365, haga clic en **Administración**.</span><span class="sxs-lookup"><span data-stu-id="a1857-169">From the Office 365 portal page, click **Admin**.</span></span>
    
18. <span data-ttu-id="a1857-170">Haga clic en el icono **seguridad &amp; y cumplimiento** .</span><span class="sxs-lookup"><span data-stu-id="a1857-170">Click the **Security &amp; Compliance** tile.</span></span>
    
19. <span data-ttu-id="a1857-171">En el panel de navegación izquierdo, haga clic en **alertas > de administración de alertas avanzadas**.</span><span class="sxs-lookup"><span data-stu-id="a1857-171">In the left navigation pane, click **Alerts > Manage advanced alerts**.</span></span>
    
20. <span data-ttu-id="a1857-172">En la página **Administrar alertas avanzadas** , haga clic en **ir a Office 365 Cloud App Security**.</span><span class="sxs-lookup"><span data-stu-id="a1857-172">On the **Manage advanced alerts** page, click **Go to Office 365 Cloud App Security**.</span></span>
    
21. <span data-ttu-id="a1857-173">En la pestaña nuevo **Panel** , observe las dos nuevas alertas de **actividad administrativa**.</span><span class="sxs-lookup"><span data-stu-id="a1857-173">On the new **Dashboard** tab, notice the two new alerts for **Administrative activity**.</span></span>
    
22. <span data-ttu-id="a1857-174">En la pestaña **Página principal de Microsoft Office** , haga clic en **correo**.</span><span class="sxs-lookup"><span data-stu-id="a1857-174">From the **Microsoft Office Home** tab, click **Mail**.</span></span> <span data-ttu-id="a1857-175">Espere unos 30 minutos.</span><span class="sxs-lookup"><span data-stu-id="a1857-175">Wait up to 30 minutes.</span></span> 
    
    <span data-ttu-id="a1857-176">Verá dos nuevos mensajes de correo electrónico en la bandeja de entrada con el título **servicio de notificación de Microsoft Azure ad**.</span><span class="sxs-lookup"><span data-stu-id="a1857-176">You should see two new email messages in the inbox with the title **Microsoft Azure AD Notification Service**.</span></span> <span data-ttu-id="a1857-177">Un mensaje indica que la cuenta de usuario 5 se ha agregado a la función de **Administrador de contraseña** y otro mensaje indica que la cuenta de usuario 5 se ha agregado a la función de **Administrador** de usuarios (igual al rol de administrador de administración de usuarios en el Centro de administración de Office 365</span><span class="sxs-lookup"><span data-stu-id="a1857-177">One message indicates that the User 5 account was added to the **Password Administrator** role and another message indicates that the User 5 account was added to the **User Administrator** role (equal to the User management administrator role in the Office 365 Admin center).</span></span>
    
<span data-ttu-id="a1857-178">Ahora puede usar este entorno para crear nuevas directivas y seguir probando con Office 365 Cloud App Security.</span><span class="sxs-lookup"><span data-stu-id="a1857-178">You can now use this environment to create new policies and further experiment with Office 365 Cloud App Security.</span></span> <span data-ttu-id="a1857-179">Vea [Get Ready for Office 365 Cloud App Security](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a) para obtener vínculos a artículos de configuración adicionales.</span><span class="sxs-lookup"><span data-stu-id="a1857-179">See [Get ready for Office 365 Cloud App Security](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a) for links to additional configuration articles.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a1857-180">Vea también</span><span class="sxs-lookup"><span data-stu-id="a1857-180">See Also</span></span>

[<span data-ttu-id="a1857-181">Guías del entorno de pruebas de adopción de la nube (TLG)</span><span class="sxs-lookup"><span data-stu-id="a1857-181">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="a1857-182">Entorno de desarrollo y prueba de Office 365</span><span class="sxs-lookup"><span data-stu-id="a1857-182">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="a1857-183">Adopción de la nube y soluciones híbridas</span><span class="sxs-lookup"><span data-stu-id="a1857-183">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="a1857-184">Información general sobre Cloud App Security en Office 365</span><span class="sxs-lookup"><span data-stu-id="a1857-184">Overview of Cloud App Security in Office 365</span></span>](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)


