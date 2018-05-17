---
title: Inscribirse iOS y Android dispositivos en su entorno de desarrollo y prueba de Microsoft Enterprise 365
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
ms.openlocfilehash: 8765a7ffb1bff1f257d7cd1ce5181561c2cf0080
ms.sourcegitcommit: 771f227d3049498fcbd7cfbeaf649e3d77e73c86
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-devtest-environment"></a><span data-ttu-id="cadf8-103">Inscribirse iOS y Android dispositivos en su entorno de desarrollo y prueba de Microsoft Enterprise 365</span><span class="sxs-lookup"><span data-stu-id="cadf8-103">Enroll iOS and Android devices in your Microsoft Enterprise 365 dev/test environment</span></span>

 <span data-ttu-id="cadf8-104">**Resumen:** Use esta guía de laboratorio de prueba para inscribirse dispositivos en su entorno de desarrollo y prueba de Microsoft 365 y administrar de forma remota.</span><span class="sxs-lookup"><span data-stu-id="cadf8-104">**Summary:** Use this Test Lab Guide to enroll devices in your Microsoft 365 dev/test environment and manage them remotely.</span></span>
  
<span data-ttu-id="cadf8-p101">El conjunto de aplicaciones de movilidad de Microsoft Enterprise (EMS) ayuda a mantener la productividad con sus aplicaciones favoritas y dispositivos durante la protección de datos de la organización de los empleados. Para obtener más información, vea [Enterprise movilidad + seguridad (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span><span class="sxs-lookup"><span data-stu-id="cadf8-p101">The Microsoft Enterprise Mobility Suite (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="cadf8-p102">Si necesita aplicar la seguridad en el nivel de dispositivo, debe inscribirse dispositivos en Microsoft Intune. Inscripción de dispositivo no sólo le ayuda a administrar los dispositivos de propiedad de la organización, pero también personal (BYOD) y dispositivos compartidos, dependiendo de la organización del departamento legal directivas.</span><span class="sxs-lookup"><span data-stu-id="cadf8-p102">If you need to apply security at the device level, you must enroll devices into Microsoft Intune. Device enrollment not only helps you to manage organization-owned devices, but also personal (BYOD) and shared devices, depending on your organization's legal policies.</span></span>
  
<span data-ttu-id="cadf8-109">Siguiendo las instrucciones proporcionadas en este artículo, podrá inscribirse y capacidades de administración de dispositivo móvil básica para iOS y Android dispositivos de prueba en el entorno de desarrollo y prueba de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="cadf8-109">By following the instructions provided in this article, you'll be able to enroll and test basic mobile device management capabilities for iOS and Android devices in your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a><span data-ttu-id="cadf8-110">Fase 1: Crear el entorno de desarrollo y prueba de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="cadf8-110">Phase 1: Create your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="cadf8-111">Siga las instrucciones que aparecen en el [entorno de desarrollo o prueba de la empresa de 365 de Microsoft](the-microsoft-365-enterprise-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="cadf8-111">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a><span data-ttu-id="cadf8-112">Fase 2: Inscribirse los dispositivos Android y iOS</span><span class="sxs-lookup"><span data-stu-id="cadf8-112">Phase 2: Enroll your iOS and Android devices</span></span>

<span data-ttu-id="cadf8-113">En primer lugar, use las instrucciones de [instalar e inicie sesión en la aplicación de Portal de empresa](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) para personalizar la aplicación de Portal de empresa de Microsoft Intune para el inquilino de desarrollo o prueba.</span><span class="sxs-lookup"><span data-stu-id="cadf8-113">First, use the instructions in [Install and sign in to the Company Portal app](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) to customize the Microsoft Intune Company Portal app for your dev/test tenant.</span></span>

<span data-ttu-id="cadf8-114">A continuación, siga las instrucciones de [Configurar el acceso a los recursos de empresa](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) para inscribirse en un dispositivo de iOS.</span><span class="sxs-lookup"><span data-stu-id="cadf8-114">Next, use the instructions in [Set up access to your company resources](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) to enroll an iOS device.</span></span>

<span data-ttu-id="cadf8-115">A continuación, siga las instrucciones de [inscripción su dispositivo Android en Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) para inscribirse en un dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="cadf8-115">Next, use the instructions in [Enroll your Android device in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) to enroll an Android device.</span></span>

## <a name="phase-2-manage-your-ios-and-android-devices-remotely"></a><span data-ttu-id="cadf8-116">Fase 2: Administrar su iOS y Android dispositivos de forma remota</span><span class="sxs-lookup"><span data-stu-id="cadf8-116">Phase 2: Manage your iOS and Android devices remotely</span></span>

<span data-ttu-id="cadf8-p103">Microsoft Intune proporciona capacidades de restablecimiento de código de acceso y bloqueo remoto. Si alguien pierde su dispositivo, puede bloquearlo de forma remota. Si alguien olvida su código de acceso, puede eliminar el código de forma remota.</span><span class="sxs-lookup"><span data-stu-id="cadf8-p103">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can remove the passcode remotely.</span></span>
  
<span data-ttu-id="cadf8-120">Para bloquear de forma remota un dispositivo iOS:</span><span class="sxs-lookup"><span data-stu-id="cadf8-120">To lock an iOS device remotely:</span></span>
  
1.  <span data-ttu-id="cadf8-121">Abra una nueva ficha y vaya a http://manage.microsoft.com (si es necesario).</span><span class="sxs-lookup"><span data-stu-id="cadf8-121">Open a new tab and go to http://manage.microsoft.com (if needed).</span></span> 

2.  <span data-ttu-id="cadf8-122">Desde la consola de administración de Microsoft Intune del explorador, haga clic en **grupos** en el panel de navegación izquierdo.</span><span class="sxs-lookup"><span data-stu-id="cadf8-122">From the Microsoft Intune administration console of your browser, click **Groups** in the left navigation.</span></span>

3. <span data-ttu-id="cadf8-123">En el panel **grupos** , abra **todos los dispositivos > dispositivos móviles todos > todos los dispositivos directa administrado**.</span><span class="sxs-lookup"><span data-stu-id="cadf8-123">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
4. <span data-ttu-id="cadf8-124">En el panel de **Todos los dispositivos administrados de directa** , haga clic en la ficha **dispositivos** .</span><span class="sxs-lookup"><span data-stu-id="cadf8-124">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
5. <span data-ttu-id="cadf8-125">En la lista de dispositivos, haga clic en su dispositivo iOS. </span><span class="sxs-lookup"><span data-stu-id="cadf8-125">In the devices list, click your iOS device.</span></span> 
    
6. <span data-ttu-id="cadf8-126">En su dispositivo iOS, asegúrese de que está en la pantalla principal. </span><span class="sxs-lookup"><span data-stu-id="cadf8-126">From your iOS device, make sure it is at the main screen.</span></span> 
    
7. <span data-ttu-id="cadf8-p104">Desde el equipo de administración, en la barra de tareas, haga clic en **tareas remotas > bloqueo remoto**. Vea su dispositivo iOS tal y como lo pasa a la pantalla de bloqueo.</span><span class="sxs-lookup"><span data-stu-id="cadf8-p104">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. Watch your iOS device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="cadf8-129">Para eliminar el código de acceso:</span><span class="sxs-lookup"><span data-stu-id="cadf8-129">To remove the passcode:</span></span>
  
1. <span data-ttu-id="cadf8-130">Desde el equipo de administración, en el panel de **Todos los dispositivos administrados de directa** , haga clic en la ficha **dispositivos** .</span><span class="sxs-lookup"><span data-stu-id="cadf8-130">From your administration computer, in the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
2. <span data-ttu-id="cadf8-p105">En la lista, haga clic en el dispositivo iOS. En la barra de tareas, haga clic en **tareas remotas > Restablecer el código de acceso**. Espere un minuto.</span><span class="sxs-lookup"><span data-stu-id="cadf8-p105">In the list, click your iOS device. On the taskbar, click **Remote Tasks > Passcode Reset**. Wait for one minute.</span></span>
    
3. <span data-ttu-id="cadf8-p106">Desde su dispositivo iOS, desbloquearlo y observe que ya no es un código de acceso. Para cambiar la copia el código de acceso, vaya a **configuración**y, a continuación, **el código de acceso**.</span><span class="sxs-lookup"><span data-stu-id="cadf8-p106">From your iOS device, unlock it and notice that there is no longer a passcode. To change the passcode back, go into **Settings**, and then **Passcode**.</span></span>
    
<span data-ttu-id="cadf8-136">Para bloquear de forma remota un dispositivo Android:</span><span class="sxs-lookup"><span data-stu-id="cadf8-136">To lock an Android device remotely:</span></span>
  
1. <span data-ttu-id="cadf8-137">Desde la consola de administración de Microsoft Intune del explorador, haga clic en **grupos** en el panel de navegación izquierdo.</span><span class="sxs-lookup"><span data-stu-id="cadf8-137">From the Microsoft Intune administration console of your browser, click **Groups** in the left navigation.</span></span>
    
2. <span data-ttu-id="cadf8-138">En el panel **grupos** , abra **todos los dispositivos > dispositivos móviles todos > todos los dispositivos directa administrado**.</span><span class="sxs-lookup"><span data-stu-id="cadf8-138">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
3. <span data-ttu-id="cadf8-139">En el panel de **Todos los dispositivos administrados de directa** , haga clic en la ficha **dispositivos** .</span><span class="sxs-lookup"><span data-stu-id="cadf8-139">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
4. <span data-ttu-id="cadf8-140">En la lista de dispositivos, haga clic en su dispositivo Android. </span><span class="sxs-lookup"><span data-stu-id="cadf8-140">In the devices list, click your Android device.</span></span> 
    
5. <span data-ttu-id="cadf8-141">En su dispositivo Android, asegúrese de que está en la pantalla principal. </span><span class="sxs-lookup"><span data-stu-id="cadf8-141">From your Android device, make sure it is at the main screen.</span></span> 
    
6. <span data-ttu-id="cadf8-p107">Desde el equipo de administración, en la barra de tareas, haga clic en **tareas remotas > bloqueo remoto**. Cuando se le solicite, haga clic en **Sí**.</span><span class="sxs-lookup"><span data-stu-id="cadf8-p107">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. When prompted, click **Yes**.</span></span>
    
7. <span data-ttu-id="cadf8-144">Observe su dispositivo Android mientras cambia a la pantalla de bloqueo.</span><span class="sxs-lookup"><span data-stu-id="cadf8-144">Watch your Android device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="cadf8-145">Cuando se restablece el código de acceso para dispositivos Android, el portal de administración Intune genera y configura un código de acceso seguro.</span><span class="sxs-lookup"><span data-stu-id="cadf8-145">When you reset the passcode for Android devices, the Intune administration portal generates and configures a strong passcode.</span></span>
  
<span data-ttu-id="cadf8-146">Para restablecer el código de acceso de forma remota:</span><span class="sxs-lookup"><span data-stu-id="cadf8-146">To reset the passcode remotely:</span></span>
  
1. <span data-ttu-id="cadf8-147">Desde el equipo de administración, en la ficha de consola de administración de Microsoft Intune del explorador, en el panel de **Todos los dispositivos administrados de directa** , haga clic en su dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="cadf8-147">From your administration computer, on the Microsoft Intune administration console tab of your browser, in the **All Direct Managed Devices** pane, click your Android device.</span></span>
    
2. <span data-ttu-id="cadf8-148">En la barra de tareas, haga clic en **tareas remotas > Restablecer el código de acceso**.</span><span class="sxs-lookup"><span data-stu-id="cadf8-148">On the taskbar, click **Remote Tasks > Passcode Reset**.</span></span>
    
3. <span data-ttu-id="cadf8-p108">En la **tarea remota: restablecer el código de acceso** el mensaje, haga clic en **Sí**. Espere un minuto.</span><span class="sxs-lookup"><span data-stu-id="cadf8-p108">On the **Remote Task: Passcode Reset** prompt, click **Yes**. Wait for one minute.</span></span>
    
4. <span data-ttu-id="cadf8-151">En el panel de **Todos los dispositivos administrados de directa** , haga clic en **Ver propiedades**.</span><span class="sxs-lookup"><span data-stu-id="cadf8-151">In the **All Direct Managed Devices** pane, click **View Properties**.</span></span>
    
5. <span data-ttu-id="cadf8-152">Bajo **Restablecer el código de acceso**, tenga en cuenta la nueva contraseña.</span><span class="sxs-lookup"><span data-stu-id="cadf8-152">Under **Passcode Reset**, note the new passcode.</span></span>
    
6. <span data-ttu-id="cadf8-153">En su dispositivo Android, introduzca el nuevo código de acceso en la pantalla de bloqueo. </span><span class="sxs-lookup"><span data-stu-id="cadf8-153">From your Android device, enter the new passcode from the lockout screen.</span></span> 
    
7. <span data-ttu-id="cadf8-154">Para cambiar el código de acceso atrás, vaya a **configuración**, puntee en el **dispositivo**, puntee en la **pantalla de bloqueo**, escriba la nueva contraseña, puntee en **bloqueo de pantalla**y, a continuación, en su elección para el código de acceso.</span><span class="sxs-lookup"><span data-stu-id="cadf8-154">To change the passcode back, go into **Settings**, tap **Device**, tap **Lock screen**, enter the new passcode again, tap **Screen lock**, and then your choice for the passcode.</span></span>
    

> [!TIP]
> <span data-ttu-id="cadf8-155">Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual de todos los artículos en la pila de la Guía del entorno de pruebas de One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="cadf8-155">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="cadf8-156">Consulte también</span><span class="sxs-lookup"><span data-stu-id="cadf8-156">See Also</span></span>

[<span data-ttu-id="cadf8-157">Entorno de pruebas y desarrollo de Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="cadf8-157">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="cadf8-158">Directivas MAM para sus entornos de desarrollo y prueba de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="cadf8-158">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="cadf8-159">Guías de entorno de pruebas de adopción de la nube (TLG)</span><span class="sxs-lookup"><span data-stu-id="cadf8-159">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="cadf8-160">Movilidad de la empresa + seguridad (EMS)</span><span class="sxs-lookup"><span data-stu-id="cadf8-160">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


