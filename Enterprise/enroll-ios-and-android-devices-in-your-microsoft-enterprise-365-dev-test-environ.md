---
title: Inscriba los dispositivos iOS y Android en el entorno de desarrollo y prueba de Microsoft 365 Enterprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/20/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: 'Resumen: Use esta guía de laboratorio de prueba para inscribirse dispositivos en su entorno de desarrollo y prueba de Microsoft 365 y administrar de forma remota.'
ms.openlocfilehash: e4b8491a70d0d0177e0a434d228136243201e788
ms.sourcegitcommit: c3869a332512dd1cc25cd5a92a340050f1da0418
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/20/2018
ms.locfileid: "20720416"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="c779f-103">Inscriba los dispositivos iOS y Android en el entorno de desarrollo y prueba de Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="c779f-103">Enroll iOS and Android devices in your Microsoft 365 Enterprise dev/test environment</span></span>

 <span data-ttu-id="c779f-104">**Resumen:** Use esta guía de laboratorio de prueba para inscribirse dispositivos en su entorno de desarrollo y prueba de Microsoft 365 y administrar de forma remota.</span><span class="sxs-lookup"><span data-stu-id="c779f-104">**Summary:** Use this Test Lab Guide to enroll devices in your Microsoft 365 dev/test environment and manage them remotely.</span></span>
  
<span data-ttu-id="c779f-p101">El conjunto de aplicaciones de movilidad de Microsoft Enterprise (EMS) ayuda a mantener la productividad con sus aplicaciones favoritas y dispositivos durante la protección de datos de la organización de los empleados. Para obtener más información, vea [Enterprise movilidad + seguridad (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span><span class="sxs-lookup"><span data-stu-id="c779f-p101">The Microsoft Enterprise Mobility Suite (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="c779f-p102">Si necesita aplicar la seguridad en el nivel de dispositivo, debe inscribirse dispositivos en Microsoft Intune. Inscripción de dispositivo no sólo le ayuda a administrar los dispositivos de propiedad de la organización, pero también personal (BYOD) y dispositivos compartidos, dependiendo de la organización del departamento legal directivas.</span><span class="sxs-lookup"><span data-stu-id="c779f-p102">If you need to apply security at the device level, you must enroll devices into Microsoft Intune. Device enrollment not only helps you to manage organization-owned devices, but also personal (BYOD) and shared devices, depending on your organization's legal policies.</span></span>
  
<span data-ttu-id="c779f-109">Siguiendo las instrucciones proporcionadas en este artículo, podrá inscribirse y capacidades de administración de dispositivo móvil básica para iOS y Android dispositivos de prueba en el entorno de desarrollo y prueba de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="c779f-109">By following the instructions provided in this article, you'll be able to enroll and test basic mobile device management capabilities for iOS and Android devices in your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a><span data-ttu-id="c779f-110">Fase 1: Crear el entorno de desarrollo y prueba de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="c779f-110">Phase 1: Create your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="c779f-111">Siga las instrucciones que aparecen en el [entorno de desarrollo o prueba de la empresa de 365 de Microsoft](the-microsoft-365-enterprise-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="c779f-111">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a><span data-ttu-id="c779f-112">Fase 2: Inscribirse los dispositivos Android y iOS</span><span class="sxs-lookup"><span data-stu-id="c779f-112">Phase 2: Enroll your iOS and Android devices</span></span>

<span data-ttu-id="c779f-113">En primer lugar, use las instrucciones de [instalar e inicie sesión en la aplicación de Portal de empresa](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) para personalizar la aplicación de Portal de empresa de Microsoft Intune para su entorno de prueba.</span><span class="sxs-lookup"><span data-stu-id="c779f-113">First, use the instructions in [Install and sign in to the Company Portal app](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) to customize the Microsoft Intune Company Portal app for your test environment.</span></span>

<span data-ttu-id="c779f-114">A continuación, siga las instrucciones de [Configurar el acceso a los recursos de empresa](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) para inscribirse en un dispositivo de iOS.</span><span class="sxs-lookup"><span data-stu-id="c779f-114">Next, use the instructions in [Set up access to your company resources](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) to enroll an iOS device.</span></span>

<span data-ttu-id="c779f-115">A continuación, siga las instrucciones de [inscripción su dispositivo Android en Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) para inscribirse en un dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="c779f-115">Next, use the instructions in [Enroll your Android device in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) to enroll an Android device.</span></span>

## <a name="phase-3-manage-your-ios-and-android-devices-remotely"></a><span data-ttu-id="c779f-116">Fase 3: Administrar su iOS y Android dispositivos de forma remota</span><span class="sxs-lookup"><span data-stu-id="c779f-116">Phase 3: Manage your iOS and Android devices remotely</span></span>

<span data-ttu-id="c779f-p103">Microsoft Intune proporciona capacidades de restablecimiento de bloqueo remoto y código de acceso. Si alguien pierde su dispositivo, puede bloquear el dispositivo de forma remota. Si alguien olvida su código de acceso, puede restablecer de forma remota.</span><span class="sxs-lookup"><span data-stu-id="c779f-p103">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can reset it remotely.</span></span>
  
<span data-ttu-id="c779f-120">Para bloquear una iOS o Android dispositivo de forma remota:</span><span class="sxs-lookup"><span data-stu-id="c779f-120">To lock an iOS or Android device remotely:</span></span>

1. <span data-ttu-id="c779f-121">Inicie sesión en el portal de Azure en [https://portal.azure.com](https://portal.azure.com) con las credenciales de su cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="c779f-121">Sign in to the Azure portal at [https://portal.azure.com](https://portal.azure.com) with the credentials of your global administrator account.</span></span>
2. <span data-ttu-id="c779f-122">Haga clic en **todos los servicios**, escriba **Intune**y, a continuación, haga clic en **Intune**.</span><span class="sxs-lookup"><span data-stu-id="c779f-122">Click **All services**, type **Intune**, and then click **Intune**.</span></span>
3. <span data-ttu-id="c779f-123">Haga clic en **dispositivos > todos los dispositivos**.</span><span class="sxs-lookup"><span data-stu-id="c779f-123">Click **Devices > All devices**.</span></span>
4. <span data-ttu-id="c779f-124">En la lista de dispositivos, haga clic en un dispositivo Android o iOS y, a continuación, haga clic en la acción de **bloqueo remoto** .</span><span class="sxs-lookup"><span data-stu-id="c779f-124">In the list of devices, click an iOS or Android device, and then click the **Remote lock** action.</span></span>

    
<span data-ttu-id="c779f-125">Para restablecer el código de acceso de forma remota:</span><span class="sxs-lookup"><span data-stu-id="c779f-125">To reset the passcode remotely:</span></span>

1. <span data-ttu-id="c779f-126">Si es necesario, inicie sesión en el portal de Azure en [https://portal.azure.com](https://portal.azure.com) con las credenciales de su cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="c779f-126">If needed, sign in to the Azure portal at [https://portal.azure.com](https://portal.azure.com) with the credentials of your global administrator account.</span></span>
2. <span data-ttu-id="c779f-127">Haga clic en **todos los servicios**, escriba **Intune**y, a continuación, haga clic en **Intune**.</span><span class="sxs-lookup"><span data-stu-id="c779f-127">Click **All services**, type **Intune**, and then click **Intune**.</span></span>
3. <span data-ttu-id="c779f-128">Haga clic en **dispositivos > todos los dispositivos**.</span><span class="sxs-lookup"><span data-stu-id="c779f-128">Click **Devices > All devices**.</span></span>
4. <span data-ttu-id="c779f-p104">En la lista de los dispositivos de administrar, haga clic en un dispositivo Android o iOS y elija **... Más**. A continuación, elija la acción **quitar el código de acceso de** dispositivo remota.</span><span class="sxs-lookup"><span data-stu-id="c779f-p104">From the list of devices you manage, click an iOS or Android device, and choose **...More**. Then choose the **Remove passcode** device remote action.</span></span>

<span data-ttu-id="c779f-131">Para realizar otras pruebas, consulte [acciones de dispositivo disponible](https://docs.microsoft.com/intune/device-management#available-device-actions).</span><span class="sxs-lookup"><span data-stu-id="c779f-131">For additional experimentation, see [Available device actions](https://docs.microsoft.com/intune/device-management#available-device-actions).</span></span>

    

> [!TIP]
> <span data-ttu-id="c779f-132">Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual de todos los artículos en la pila de la Guía del entorno de pruebas de One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="c779f-132">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c779f-133">Consulte también</span><span class="sxs-lookup"><span data-stu-id="c779f-133">See Also</span></span>

[<span data-ttu-id="c779f-134">Entorno de pruebas y desarrollo de Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="c779f-134">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="c779f-135">Directivas MAM para sus entornos de desarrollo y prueba de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="c779f-135">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="c779f-136">Guías de entorno de pruebas de adopción de la nube (TLG)</span><span class="sxs-lookup"><span data-stu-id="c779f-136">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="c779f-137">Movilidad de la empresa + seguridad (EMS)</span><span class="sxs-lookup"><span data-stu-id="c779f-137">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


