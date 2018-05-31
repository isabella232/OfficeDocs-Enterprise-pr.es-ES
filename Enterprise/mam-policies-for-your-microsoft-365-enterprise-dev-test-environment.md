---
title: Directivas de MAM para el entorno de desarrollo y prueba de Microsoft 365 Enterprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: 'Resumen: Use esta guía de laboratorio de prueba para agregar las directivas de administración (MAM) de una aplicación móvil de EMS a su entorno de desarrollo y prueba de Microsoft 365.'
ms.openlocfilehash: 1d4ede9b5757d4adce8909586790bcad51f7433f
ms.sourcegitcommit: 29c8571ca4912549bac55ec9d1642d21eba5b0e4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2018
ms.locfileid: "19168534"
---
# <a name="mam-policies-for-your-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="05490-103">Directivas de MAM para el entorno de desarrollo y prueba de Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="05490-103">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>

 <span data-ttu-id="05490-104">**Resumen:** Use esta guía de laboratorio de prueba para agregar las directivas de administración (MAM) de una aplicación móvil de EMS a su entorno de desarrollo y prueba de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="05490-104">**Summary:** Use this Test Lab Guide to add EMS mobile application management (MAM) policies to your Microsoft 365 dev/test environment.</span></span>
  
<span data-ttu-id="05490-p101">La movilidad de Microsoft Enterprise + seguridad (EMS) ayuda a mantener la productividad con sus aplicaciones favoritas y dispositivos durante la protección de datos de la organización de los empleados. Para obtener más información, vea [Enterprise movilidad + seguridad (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span><span class="sxs-lookup"><span data-stu-id="05490-p101">The Microsoft Enterprise Mobility + Security (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="05490-107">Con las instrucciones de este artículo, agregue las directivas de administración (MAM) de aplicaciones móviles a su entorno de desarrollo y prueba de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="05490-107">With the instructions in this article, you add mobile application management (MAM) policies to your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-build-out-your-microsoft-365-devtest-environment"></a><span data-ttu-id="05490-108">Fase 1: Generar el entorno de desarrollo y prueba de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="05490-108">Phase 1: Build out your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="05490-109">Siga las instrucciones que aparecen en el [entorno de desarrollo o prueba de la empresa de 365 de Microsoft](the-microsoft-365-enterprise-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="05490-109">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-create-and-deploy-mam-policies-for-ios-and-android-devices"></a><span data-ttu-id="05490-110">Fase 2: Crear e implementar directivas de MAM para dispositivos iOS y Android</span><span class="sxs-lookup"><span data-stu-id="05490-110">Phase 2: Create and deploy MAM policies for iOS and Android devices</span></span>

<span data-ttu-id="05490-111">En esta fase, creará e implementará dos directivas de MAM diferentes: una para dispositivos iOS y otra para dispositivos Android.</span><span class="sxs-lookup"><span data-stu-id="05490-111">In this phase, you create and deploy two different MAM policies: one for iOS devices and one for Android devices.</span></span>
  
1. <span data-ttu-id="05490-112">Vaya al portal de Office 365 ([https://portal.office.com](https://portal.office.com)) e inicie sesión en su suscripción de prueba de Office 365 con su cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="05490-112">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="05490-113">En una nueva ficha del explorador, abra el portal de Azure ([https://azure.portal.com](https://azure.portal.com)) e iniciar sesión con su cuenta de administrador global de Office 365.</span><span class="sxs-lookup"><span data-stu-id="05490-113">On a new tab of your browser, open the Azure portal ([https://azure.portal.com](https://azure.portal.com)) and sign in using your Office 365 global administrator account.</span></span>
    
3. <span data-ttu-id="05490-114">En la ficha portal Azure en Internet Explorer, en el panel de navegación, haga clic en **todos los servicios**, escriba **Intune**y, a continuación, haga clic en **Intune**.</span><span class="sxs-lookup"><span data-stu-id="05490-114">On the Azure portal tab in Internet Explorer, in the navigation pane, click **All services**, type **Intune**, and then click **Intune**.</span></span>
    
4. <span data-ttu-id="05490-115">En el panel de navegación izquierdo, haga clic en **Grupos**.</span><span class="sxs-lookup"><span data-stu-id="05490-115">In the left navigation pane, click **Groups**.</span></span>
    
5. <span data-ttu-id="05490-116">En el servidor blade de **grupos a todos los grupos** , haga clic en **+ nuevo grupo**.</span><span class="sxs-lookup"><span data-stu-id="05490-116">On the **Groups-All groups** blade, click **+ New Group**.</span></span>
    
6. <span data-ttu-id="05490-117">En el servidor blade de **grupo** , seleccione **Office 365** para **tipo de grupo?**, escriba **administrado a los usuarios de dispositivos iOS** en **nombre**, seleccione **asignado** en **tipo de pertenencia**y, a continuación, haga clic en **crear**.</span><span class="sxs-lookup"><span data-stu-id="05490-117">On the **Group** blade, select **Office 365** for **Group type?**, type **Managed iOS device users** in **Name**, select **Assigned** in **Membership type**,  and then click **Create**.</span></span> 
    
7. <span data-ttu-id="05490-118">Cierre el servidor blade de **grupo** .</span><span class="sxs-lookup"><span data-stu-id="05490-118">Close the **Group** blade.</span></span>
    
8. <span data-ttu-id="05490-119">En el servidor blade de **grupos a todos los grupos** , haga clic en **Agregar**.</span><span class="sxs-lookup"><span data-stu-id="05490-119">On the **Groups-All groups** blade, click **Add**.</span></span>
    
9. <span data-ttu-id="05490-120">En el servidor blade de **grupo** , seleccione **Office 365** para **tipo de grupo?**, escriba **usuario de dispositivos Android administrado** en **nombre**, seleccione **asignado** en **tipo de pertenencia**y, a continuación, haga clic en **crear**.</span><span class="sxs-lookup"><span data-stu-id="05490-120">On the **Group** blade, select **Office 365** for **Group type?**, type **Managed Android device user** in **Name**, select **Assigned** in **Membership type**,  and then click **Create**.</span></span>
    
10. <span data-ttu-id="05490-121">Cierre el servidor blade de **grupos a todos los grupos** .</span><span class="sxs-lookup"><span data-stu-id="05490-121">Close the **Groups-All groups** blade.</span></span>
    
11. <span data-ttu-id="05490-122">En el servidor blade **Intune** , en la lista de **tareas rápidas** , haga clic en **crear una directiva de cumplimiento**.</span><span class="sxs-lookup"><span data-stu-id="05490-122">On the **Intune** blade, in the **Quick tasks** list, click **Create a compliance policy**.</span></span>
    
12. <span data-ttu-id="05490-123">En el servidor blade de **Perfiles de directivas de cumplimiento** , haga clic en **Crear directiva**.</span><span class="sxs-lookup"><span data-stu-id="05490-123">On the **Compliance Policy Profiles** blade, click **Create Policy**.</span></span>
    
13. <span data-ttu-id="05490-p102">En el módulo de **Directiva de crear** , en **nombre**, escriba **iOS**. En la **plataforma**, seleccione **iOS**, haga clic en **Aceptar** en el servidor blade de la **Directiva de cumplimiento de iOS** y, a continuación, haga clic en **crear**.</span><span class="sxs-lookup"><span data-stu-id="05490-p102">On the **Create Policy** blade, in **Name**, type **iOS**. In **Platform**, select **iOS**, click **OK** on the **iOS compliance policy** blade, and then click **Create**.</span></span>
    
14. <span data-ttu-id="05490-126">En el servidor blade de **Perfiles de directivas de cumplimiento** , haga clic en **Crear directiva**.</span><span class="sxs-lookup"><span data-stu-id="05490-126">On the **Compliance Policy Profiles** blade, click **Create Policy**.</span></span>
    
15. <span data-ttu-id="05490-p103">En el módulo de **Directiva de crear** , en **nombre**, escriba **Android**. En la **plataforma**, seleccione **Android**, haga clic en **Aceptar** en la **Directiva de cumplimiento Android** blade y, a continuación, haga clic en **crear**.</span><span class="sxs-lookup"><span data-stu-id="05490-p103">On the **Create Policy** blade, in **Name**, type **Android**. In **Platform**, select **Android**, click **OK** on the **Android compliance policy** blade, and then click **Create**.</span></span>
    
16. <span data-ttu-id="05490-129">En el servidor blade de **Perfiles de directivas de cumplimiento** , haga clic en el nombre de directiva **para Android** .</span><span class="sxs-lookup"><span data-stu-id="05490-129">On the **Compliance Policy Profiles** blade, click the **Android** policy name.</span></span>
    
17. <span data-ttu-id="05490-130">En la izquierda el blade **Android - propiedades** , haga clic en **asignaciones**y, a continuación, haga clic en **Seleccionar grupos**.</span><span class="sxs-lookup"><span data-stu-id="05490-130">In the left navigation of the **Android - Properties** blade, click **Assignments**, and then click **Select groups**.</span></span>
    
18. <span data-ttu-id="05490-131">En el servidor blade **Seleccionar grupos** , haga clic en el grupo de **usuarios de dispositivos Android administrados** y, a continuación, haga clic en **Seleccionar**.</span><span class="sxs-lookup"><span data-stu-id="05490-131">On the **Select groups** blade, click the **Managed Android device users** group, and then click **Select**.</span></span>
    
19. <span data-ttu-id="05490-132">Haga clic en **Guardar**y, a continuación, cierre el blade **Android - las asignaciones** .</span><span class="sxs-lookup"><span data-stu-id="05490-132">Click **Save**, and then close the **Android - Assignments** blade.</span></span>
    
20. <span data-ttu-id="05490-133">En el servidor blade de **Perfiles de directivas de cumplimiento** , haga clic en el nombre de la directiva de **iOS** .</span><span class="sxs-lookup"><span data-stu-id="05490-133">On the **Compliance Policy Profiles** blade, click the **iOS** policy name.</span></span>
    
21. <span data-ttu-id="05490-134">En la izquierda el blade **iOS - propiedades** , haga clic en **asignaciones**y, a continuación, haga clic en **Seleccionar grupos**.</span><span class="sxs-lookup"><span data-stu-id="05490-134">In the left navigation of the **iOS - Properties** blade, click **Assignments**, and then click **Select groups**.</span></span>
    
22. <span data-ttu-id="05490-135">En el servidor blade **Seleccionar grupos** , haga clic en el grupo de **usuarios de dispositivos de Managed iOS** y, a continuación, haga clic en **Seleccionar**.</span><span class="sxs-lookup"><span data-stu-id="05490-135">On the **Select groups** blade, click the **Managed iOS device users** group, and then click **Select**.</span></span>
    
23. <span data-ttu-id="05490-136">Haga clic en **Guardar**y, a continuación, cierre el blade **iOS - las asignaciones** .</span><span class="sxs-lookup"><span data-stu-id="05490-136">Click **Save**, and then close the **iOS - Assignments** blade.</span></span>
    
24. <span data-ttu-id="05490-137">Cierre el servidor blade de **Perfiles de directivas de cumplimiento de normas** .</span><span class="sxs-lookup"><span data-stu-id="05490-137">Close the **Compliance Policy Profiles** blade.</span></span>
    
25. <span data-ttu-id="05490-138">En el servidor blade **Intune** , haga clic en **Administrar aplicaciones** en el panel de navegación izquierdo.</span><span class="sxs-lookup"><span data-stu-id="05490-138">On the **Intune** blade, click **Manage apps** in the left navigation.</span></span>
    
26. <span data-ttu-id="05490-139">En el módulo de **Aplicaciones de Mobile** , haga clic en **aplicaciones**.</span><span class="sxs-lookup"><span data-stu-id="05490-139">On the **Mobile Apps** blade, click **Apps**.</span></span>
    
27. <span data-ttu-id="05490-140">En la lista de aplicaciones, haga clic en **PowerPoint**,</span><span class="sxs-lookup"><span data-stu-id="05490-140">In the list of apps, click **PowerPoint**,</span></span> 
    
28. <span data-ttu-id="05490-p104">En el servidor blade de **Introducción a PowerPoint** , haga clic en **asignaciones > seleccione grupos > administrados dispositivos iOS > seleccione**. En **tipo**, seleccione **disponible**y, a continuación, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="05490-p104">On the **PowerPoint Overview** blade, click **Assignments > Select groups > Managed iOS devices > Select**. In **Type**, select **Available**, and then click **Save**.</span></span>
    
29. <span data-ttu-id="05490-143">Repita el paso 28 para las aplicaciones siguientes:</span><span class="sxs-lookup"><span data-stu-id="05490-143">Repeat step 28 for the following apps:</span></span>
    
  - <span data-ttu-id="05490-144">Outlook para Android</span><span class="sxs-lookup"><span data-stu-id="05490-144">Outlook for Android</span></span>
    
  - <span data-ttu-id="05490-145">Word para iOS</span><span class="sxs-lookup"><span data-stu-id="05490-145">Word for iOS</span></span>
    
  - <span data-ttu-id="05490-146">Excel para iOS</span><span class="sxs-lookup"><span data-stu-id="05490-146">Excel for iOS</span></span>
    
  - <span data-ttu-id="05490-147">Outlook para iOS</span><span class="sxs-lookup"><span data-stu-id="05490-147">Outlook for iOS</span></span>
    
  - <span data-ttu-id="05490-148">Microsoft Dynamics CRM en iPad para iOS</span><span class="sxs-lookup"><span data-stu-id="05490-148">Microsoft Dynamics CRM on iPad for iOS</span></span>
    
  - <span data-ttu-id="05490-149">Microsoft Dynamics CRM en iPhone para iOS</span><span class="sxs-lookup"><span data-stu-id="05490-149">Microsoft Dynamics CRM on iPhone for iOS</span></span>
    
  - <span data-ttu-id="05490-150">Dynamics CRM para teléfonos Android</span><span class="sxs-lookup"><span data-stu-id="05490-150">Dynamics CRM for Phones for Android</span></span>
    
  - <span data-ttu-id="05490-151">Dynamics CRM para tabletas Android</span><span class="sxs-lookup"><span data-stu-id="05490-151">Dynamics CRM for Tablets for Android</span></span>
    
  - <span data-ttu-id="05490-152">Excel para Android</span><span class="sxs-lookup"><span data-stu-id="05490-152">Excel for Android</span></span>
    
  - <span data-ttu-id="05490-153">Word para Android</span><span class="sxs-lookup"><span data-stu-id="05490-153">Word for Android</span></span>
    
  - <span data-ttu-id="05490-154">OneNote para iOS</span><span class="sxs-lookup"><span data-stu-id="05490-154">OneNote for iOS</span></span>
    
30. <span data-ttu-id="05490-155">Cierre el blade **Mobile aplicaciones - aplicaciones** .</span><span class="sxs-lookup"><span data-stu-id="05490-155">Close the **Mobile Apps - Apps** blade.</span></span>
    
31. <span data-ttu-id="05490-156">En el módulo de **Aplicaciones de Mobile** , haga clic en **Directivas de protección de aplicaciones**.</span><span class="sxs-lookup"><span data-stu-id="05490-156">On the **Mobile Apps** blade, click **App Protection Policies**.</span></span>
    
32. <span data-ttu-id="05490-157">En el módulo de **Directivas de protección de aplicaciones** , haga clic en **Agregar una directiva**.</span><span class="sxs-lookup"><span data-stu-id="05490-157">On the **App Protection Policies** blade, click **Add a policy**.</span></span>
    
33. <span data-ttu-id="05490-158">En el servidor blade de **Agregar una directiva** , escriba **iOS**y, a continuación, haga clic en **seleccionar aplicaciones necesarias**.</span><span class="sxs-lookup"><span data-stu-id="05490-158">On the **Add a policy** blade, type **iOS**, and then click **Select required apps**.</span></span>
    
34. <span data-ttu-id="05490-159">En el servidor blade de **aplicaciones** , haga clic en **PowerPoint**, **Microsoft Dynamics CRM en iPhone**, **Excel**, **Microsoft Dynamics CRM en iPhone**, **Word**, **OneNote**y **Outlook**y, a continuación, haga clic en **Seleccionar**.</span><span class="sxs-lookup"><span data-stu-id="05490-159">On the **Apps** blade, click **PowerPoint**, **Microsoft Dynamics CRM on iPhone**, **Excel**, **Microsoft Dynamics CRM on iPhone**, **Word**, **OneNote**, and **Outlook**, and then click **Select**.</span></span>
    
35. <span data-ttu-id="05490-160">En el servidor blade de **Agregar una directiva** , haga clic en **crear**.</span><span class="sxs-lookup"><span data-stu-id="05490-160">On the **Add a policy** blade, click **Create**.</span></span>
    
36. <span data-ttu-id="05490-161">En el módulo de **Directivas de protección de aplicaciones** , haga clic en **Agregar una directiva**.</span><span class="sxs-lookup"><span data-stu-id="05490-161">On the **App Protection Policies** blade, click **Add a policy**.</span></span>
    
37. <span data-ttu-id="05490-162">En el servidor blade de **Agregar una directiva** , escriba **Android**, seleccione **Android** en la **plataforma**y, a continuación, haga clic en **seleccionar aplicaciones necesarias**.</span><span class="sxs-lookup"><span data-stu-id="05490-162">On the **Add a policy** blade, type **Android**, select **Android** in **Platform**, and then click **Select required apps**.</span></span>
    
38. <span data-ttu-id="05490-163">En el servidor blade de **aplicaciones** , haga clic en **PowerPoint**, **Dynamics CRM para tabletas**, **Excel**, **Word**, **Outlook**y **Dynamics CRM para teléfonos**y, a continuación, haga clic en **Seleccionar**.</span><span class="sxs-lookup"><span data-stu-id="05490-163">On the **Apps** blade, click **PowerPoint**, **Dynamics CRM for tablets**, **Excel**, **Word**, **Outlook**, and **Dynamics CRM for phones**, and then click **Select**.</span></span>
    
39. <span data-ttu-id="05490-164">En el servidor blade de **Agregar una directiva** , haga clic en **crear**.</span><span class="sxs-lookup"><span data-stu-id="05490-164">On the **Add a policy** blade, click **Create**.</span></span>
    
<span data-ttu-id="05490-165">Ahora tiene dos directivas de MAM, una para dispositivos iOS y otra para dispositivos Android, y está preparado para experimentar con la configuración de prueba para las aplicaciones seleccionadas.</span><span class="sxs-lookup"><span data-stu-id="05490-165">You now have two MAM policies, one for iOS devices and one for Android devices, and are ready to experiment with testing settings for the selected apps.</span></span>
  
> [!TIP]
> <span data-ttu-id="05490-166">Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual de todos los artículos en la pila de la Guía del entorno de pruebas de One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="05490-166">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="05490-167">Consulte también</span><span class="sxs-lookup"><span data-stu-id="05490-167">See Also</span></span>

[<span data-ttu-id="05490-168">Entorno de pruebas y desarrollo de Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="05490-168">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="05490-169">Inscriba sus dispositvos iOS y Android en su entorno de desarrollo y prueba de Microsoft Enterprise 365</span><span class="sxs-lookup"><span data-stu-id="05490-169">Enroll iOS and Android devices in your Microsoft Enterprise 365 dev/test environment</span></span>](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[<span data-ttu-id="05490-170">Guías de entorno de pruebas de adopción de la nube (TLG)</span><span class="sxs-lookup"><span data-stu-id="05490-170">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="05490-171">Movilidad de la empresa + seguridad (EMS)</span><span class="sxs-lookup"><span data-stu-id="05490-171">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


