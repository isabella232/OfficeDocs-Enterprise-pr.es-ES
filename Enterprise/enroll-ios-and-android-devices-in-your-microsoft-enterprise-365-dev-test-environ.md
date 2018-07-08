---
title: Inscriba los dispositivos iOS y Android en el entorno de desarrollo y prueba de Microsoft 365 Enterprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/14/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: 'Resumen: Use esta guía de laboratorio de prueba para inscribirse dispositivos en su entorno de desarrollo y prueba de Microsoft 365 y administrar de forma remota.'
ms.openlocfilehash: a5d43a0ef3ed090f84c8415de3ac26f53fdafe0a
ms.sourcegitcommit: c23b95d32a865e45be7843f38a1f23b5693ba76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2018
ms.locfileid: "20188108"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="911df-103">Inscriba los dispositivos iOS y Android en el entorno de desarrollo y prueba de Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="911df-103">Enroll iOS and Android devices in your Microsoft 365 Enterprise dev/test environment</span></span>

 <span data-ttu-id="911df-104">**Resumen:** Use esta guía de laboratorio de prueba para inscribirse dispositivos en su entorno de desarrollo y prueba de Microsoft 365 y administrar de forma remota.</span><span class="sxs-lookup"><span data-stu-id="911df-104">**Summary:** Use this Test Lab Guide to enroll devices in your Microsoft 365 dev/test environment and manage them remotely.</span></span>
  
<span data-ttu-id="911df-p101">El conjunto de aplicaciones de movilidad de Microsoft Enterprise (EMS) ayuda a mantener la productividad con sus aplicaciones favoritas y dispositivos durante la protección de datos de la organización de los empleados. Para obtener más información, vea [Enterprise movilidad + seguridad (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span><span class="sxs-lookup"><span data-stu-id="911df-p101">The Microsoft Enterprise Mobility Suite (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="911df-p102">Si necesita aplicar la seguridad en el nivel de dispositivo, debe inscribirse dispositivos en Microsoft Intune. Inscripción de dispositivo no sólo le ayuda a administrar los dispositivos de propiedad de la organización, pero también personal (BYOD) y dispositivos compartidos, dependiendo de la organización del departamento legal directivas.</span><span class="sxs-lookup"><span data-stu-id="911df-p102">If you need to apply security at the device level, you must enroll devices into Microsoft Intune. Device enrollment not only helps you to manage organization-owned devices, but also personal (BYOD) and shared devices, depending on your organization's legal policies.</span></span>
  
<span data-ttu-id="911df-109">Siguiendo las instrucciones proporcionadas en este artículo, podrá inscribirse y capacidades de administración de dispositivo móvil básica para iOS y Android dispositivos de prueba en el entorno de desarrollo y prueba de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="911df-109">By following the instructions provided in this article, you'll be able to enroll and test basic mobile device management capabilities for iOS and Android devices in your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a><span data-ttu-id="911df-110">Fase 1: Crear el entorno de desarrollo y prueba de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="911df-110">Phase 1: Create your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="911df-111">Siga las instrucciones que aparecen en el [entorno de desarrollo o prueba de la empresa de 365 de Microsoft](the-microsoft-365-enterprise-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="911df-111">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a><span data-ttu-id="911df-112">Fase 2: Inscribirse los dispositivos Android y iOS</span><span class="sxs-lookup"><span data-stu-id="911df-112">Phase 2: Enroll your iOS and Android devices</span></span>

<span data-ttu-id="911df-113">En primer lugar, use las instrucciones de [instalar e inicie sesión en la aplicación de Portal de empresa](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) para personalizar la aplicación de Portal de empresa de Microsoft Intune para el inquilino de desarrollo o prueba.</span><span class="sxs-lookup"><span data-stu-id="911df-113">First, use the instructions in [Install and sign in to the Company Portal app](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) to customize the Microsoft Intune Company Portal app for your dev/test tenant.</span></span>

<span data-ttu-id="911df-114">A continuación, siga las instrucciones de [Configurar el acceso a los recursos de empresa](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) para inscribirse en un dispositivo de iOS.</span><span class="sxs-lookup"><span data-stu-id="911df-114">Next, use the instructions in [Set up access to your company resources](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) to enroll an iOS device.</span></span>

<span data-ttu-id="911df-115">A continuación, siga las instrucciones de [inscripción su dispositivo Android en Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) para inscribirse en un dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="911df-115">Next, use the instructions in [Enroll your Android device in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) to enroll an Android device.</span></span>

## <a name="phase-2-manage-your-ios-and-android-devices-remotely"></a><span data-ttu-id="911df-116">Fase 2: Administrar su iOS y Android dispositivos de forma remota</span><span class="sxs-lookup"><span data-stu-id="911df-116">Phase 2: Manage your iOS and Android devices remotely</span></span>

<span data-ttu-id="911df-p103">Microsoft Intune proporciona capacidades de restablecimiento de código de acceso y bloqueo remoto. Si alguien pierde su dispositivo, puede bloquearlo de forma remota. Si alguien olvida su código de acceso, puede eliminar el código de forma remota.</span><span class="sxs-lookup"><span data-stu-id="911df-p103">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can remove the passcode remotely.</span></span>
  
<span data-ttu-id="911df-120">Para bloquear de forma remota un dispositivo iOS:</span><span class="sxs-lookup"><span data-stu-id="911df-120">To lock an iOS device remotely:</span></span>
  
1.  <span data-ttu-id="911df-121">Abra una nueva ficha y vaya a http://manage.microsoft.com (si es necesario).</span><span class="sxs-lookup"><span data-stu-id="911df-121">Open a new tab and go to http://manage.microsoft.com (if needed).</span></span> 

2.  <span data-ttu-id="911df-122">Desde la consola de administración de Microsoft Intune del explorador, haga clic en **grupos** en el panel de navegación izquierdo.</span><span class="sxs-lookup"><span data-stu-id="911df-122">From the Microsoft Intune administration console of your browser, click **Groups** in the left navigation.</span></span>

3. <span data-ttu-id="911df-123">En el panel **Grupos**, abra **Todos los dispositivos > Todos los dispositivos móviles > Todos los dispositivos administrados directamente**.</span><span class="sxs-lookup"><span data-stu-id="911df-123">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
4. <span data-ttu-id="911df-124">En el panel **Todos los dispositivos administrados directamente**, haga clic en la pestaña **Dispositivos**.</span><span class="sxs-lookup"><span data-stu-id="911df-124">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
5. <span data-ttu-id="911df-125">En la lista de dispositivos, haga clic en su dispositivo iOS. </span><span class="sxs-lookup"><span data-stu-id="911df-125">In the devices list, click your iOS device.</span></span> 
    
6. <span data-ttu-id="911df-126">En su dispositivo iOS, asegúrese de que está en la pantalla principal. </span><span class="sxs-lookup"><span data-stu-id="911df-126">From your iOS device, make sure it is at the main screen.</span></span> 
    
7. <span data-ttu-id="911df-p104">En el equipo de administración, en la barra de tareas, haga clic en **Tareas remotas > Bloqueo remoto**. Observe su dispositivo iOS mientras cambia a la pantalla de bloqueo.</span><span class="sxs-lookup"><span data-stu-id="911df-p104">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. Watch your iOS device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="911df-129">Para eliminar el código de acceso:</span><span class="sxs-lookup"><span data-stu-id="911df-129">To remove the passcode:</span></span>
  
1. <span data-ttu-id="911df-130">En el equipo de administración, en el panel **Todos los dispositivos administrados directamente**, haga clic en la pestaña **Dispositivos**.</span><span class="sxs-lookup"><span data-stu-id="911df-130">From your administration computer, in the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
2. <span data-ttu-id="911df-p105">En la lista, haga clic en su dispositivo iOS. En la barra de tareas, haga clic en **Tareas remotas > Restablecimiento de código de acceso**. Espere un minuto.</span><span class="sxs-lookup"><span data-stu-id="911df-p105">In the list, click your iOS device. On the taskbar, click **Remote Tasks > Passcode Reset**. Wait for one minute.</span></span>
    
3. <span data-ttu-id="911df-p106">En su dispositivo iOS, desbloquéelo y observe que ya no hay código de acceso. Para volver a cambiar el código de acceso, vaya a **Configuración** y luego **Código de acceso**.</span><span class="sxs-lookup"><span data-stu-id="911df-p106">From your iOS device, unlock it and notice that there is no longer a passcode. To change the passcode back, go into **Settings**, and then **Passcode**.</span></span>
    
<span data-ttu-id="911df-136">Para bloquear de forma remota un dispositivo Android:</span><span class="sxs-lookup"><span data-stu-id="911df-136">To lock an Android device remotely:</span></span>
  
1. <span data-ttu-id="911df-137">Desde la consola de administración de Microsoft Intune del explorador, haga clic en **grupos** en el panel de navegación izquierdo.</span><span class="sxs-lookup"><span data-stu-id="911df-137">From the Microsoft Intune administration console of your browser, click **Groups** in the left navigation.</span></span>
    
2. <span data-ttu-id="911df-138">En el panel **Grupos**, abra **Todos los dispositivos > Todos los dispositivos móviles > Todos los dispositivos administrados directamente**.</span><span class="sxs-lookup"><span data-stu-id="911df-138">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
3. <span data-ttu-id="911df-139">En el panel **Todos los dispositivos administrados directamente**, haga clic en la pestaña **Dispositivos**.</span><span class="sxs-lookup"><span data-stu-id="911df-139">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
4. <span data-ttu-id="911df-140">En la lista de dispositivos, haga clic en su dispositivo Android. </span><span class="sxs-lookup"><span data-stu-id="911df-140">In the devices list, click your Android device.</span></span> 
    
5. <span data-ttu-id="911df-141">En su dispositivo Android, asegúrese de que está en la pantalla principal. </span><span class="sxs-lookup"><span data-stu-id="911df-141">From your Android device, make sure it is at the main screen.</span></span> 
    
6. <span data-ttu-id="911df-p107">En el equipo de administración, en la barra de tareas, haga clic en **Tareas remotas > Bloqueo remoto**. Cuando se le solicite, haga clic en **Sí**.</span><span class="sxs-lookup"><span data-stu-id="911df-p107">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. When prompted, click **Yes**.</span></span>
    
7. <span data-ttu-id="911df-144">Observe su dispositivo Android mientras cambia a la pantalla de bloqueo.</span><span class="sxs-lookup"><span data-stu-id="911df-144">Watch your Android device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="911df-145">Cuando se restablece el código de acceso para dispositivos Android, el portal de administración Intune genera y configura un código de acceso seguro.</span><span class="sxs-lookup"><span data-stu-id="911df-145">When you reset the passcode for Android devices, the Intune administration portal generates and configures a strong passcode.</span></span>
  
<span data-ttu-id="911df-146">Para restablecer el código de acceso de forma remota:</span><span class="sxs-lookup"><span data-stu-id="911df-146">To reset the passcode remotely:</span></span>
  
1. <span data-ttu-id="911df-147">En el equipo de administración, en la pestaña de la consola de administración de Microsoft Intune del explorador, en el panel **Todos los dispositivos administrados directamente**, haga clic en su dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="911df-147">From your administration computer, on the Microsoft Intune administration console tab of your browser, in the **All Direct Managed Devices** pane, click your Android device.</span></span>
    
2. <span data-ttu-id="911df-148">En la barra de tareas, haga clic en **Tareas remotas > Restablecimiento de código de acceso**.</span><span class="sxs-lookup"><span data-stu-id="911df-148">On the taskbar, click **Remote Tasks > Passcode Reset**.</span></span>
    
3. <span data-ttu-id="911df-p108">En el aviso **Tarea remota: Restablecimiento de código de acceso**, haga clic en **Sí**. Espere un minuto.</span><span class="sxs-lookup"><span data-stu-id="911df-p108">On the **Remote Task: Passcode Reset** prompt, click **Yes**. Wait for one minute.</span></span>
    
4. <span data-ttu-id="911df-151">En el panel **Todos los dispositivos administrados directamente**, haga clic en **Ver propiedades**.</span><span class="sxs-lookup"><span data-stu-id="911df-151">In the **All Direct Managed Devices** pane, click **View Properties**.</span></span>
    
5. <span data-ttu-id="911df-152">En **Restablecimiento de código de acceso**, anote el nuevo código de acceso.</span><span class="sxs-lookup"><span data-stu-id="911df-152">Under **Passcode Reset**, note the new passcode.</span></span>
    
6. <span data-ttu-id="911df-153">En su dispositivo Android, introduzca el nuevo código de acceso en la pantalla de bloqueo. </span><span class="sxs-lookup"><span data-stu-id="911df-153">From your Android device, enter the new passcode from the lockout screen.</span></span> 
    
7. <span data-ttu-id="911df-154">Para volver a cambiar el código de acceso, vaya a **Configuración**, pulse **Dispositivo**, pulse **Pantalla de bloqueo**, escriba el nuevo código de acceso, pulse **Bloqueo de pantalla** y luego su elección de código de acceso.</span><span class="sxs-lookup"><span data-stu-id="911df-154">To change the passcode back, go into **Settings**, tap **Device**, tap **Lock screen**, enter the new passcode again, tap **Screen lock**, and then your choice for the passcode.</span></span>
    

> [!TIP]
> <span data-ttu-id="911df-155">Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual de todos los artículos en la pila de la Guía del entorno de pruebas de One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="911df-155">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="911df-156">Consulte también</span><span class="sxs-lookup"><span data-stu-id="911df-156">See Also</span></span>

[<span data-ttu-id="911df-157">Entorno de pruebas y desarrollo de Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="911df-157">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="911df-158">Directivas MAM para sus entornos de desarrollo y prueba de Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="911df-158">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="911df-159">Guías de entorno de pruebas de adopción de la nube (TLG)</span><span class="sxs-lookup"><span data-stu-id="911df-159">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="911df-160">Movilidad de la empresa + seguridad (EMS)</span><span class="sxs-lookup"><span data-stu-id="911df-160">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


