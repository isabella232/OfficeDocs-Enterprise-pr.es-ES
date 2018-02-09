---
title: Inscribir a dispositivos iOS y Android en su entorno de pruebas y desarrollo de Microsoft Enterprise 365
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
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: "Resumen: Utilice a esta guía de laboratorio de prueba para inscribir dispositivos en su entorno de pruebas y desarrollo de Microsoft 365 y administrar de forma remota."
ms.openlocfilehash: 77b5074b083656fdfa2cd460510231dae0689d10
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-devtest-environment"></a><span data-ttu-id="42445-103">Inscribir a dispositivos iOS y Android en su entorno de pruebas y desarrollo de Microsoft Enterprise 365</span><span class="sxs-lookup"><span data-stu-id="42445-103">Enroll iOS and Android devices in your Microsoft Enterprise 365 dev/test environment</span></span>

 <span data-ttu-id="42445-104">**Resumen:** Utilice a esta guía de laboratorio de prueba para inscribir dispositivos en su entorno de pruebas y desarrollo de Microsoft 365 y administrar de forma remota.</span><span class="sxs-lookup"><span data-stu-id="42445-104">**Summary:** Use this Test Lab Guide to enroll devices in your Microsoft 365 dev/test environment and manage them remotely.</span></span>
  
<span data-ttu-id="42445-p101">La Suite Microsoft de movilidad empresarial (EMS) ayuda a mantener la productividad con sus aplicaciones favoritas y dispositivos mientras protege los datos de la organización de sus empleados. Para obtener más información, vea [seguridad (EMS) + de movilidad en la empresa](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span><span class="sxs-lookup"><span data-stu-id="42445-p101">The Microsoft Enterprise Mobility Suite (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="42445-p102">Si necesita aplicar la seguridad en el nivel del dispositivo, debe inscribir dispositivos en Microsoft Intune. La inscripción de dispositivos no solo le ayuda a administrar dispositivos de propiedad corporativa, sino también dispositivos personales (BYOD) y compartidos, según las directivas legales de su organización.</span><span class="sxs-lookup"><span data-stu-id="42445-p102">If you need to apply security at the device level, you must enroll devices into Microsoft Intune. Device enrollment not only helps you to manage corporate-owned devices, but also personal (BYOD) and shared devices, depending on your organization's legal policies.</span></span>
  
<span data-ttu-id="42445-109">Siguiendo las instrucciones proporcionadas en este artículo, podrá inscribirse y probar las capacidades de administración básica de dispositivos móviles para dispositivos iOS y Android en su entorno de pruebas y desarrollo de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="42445-109">By following the instructions provided in this article, you'll be able to enroll and test basic mobile device management capabilities for iOS and Android devices in your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a><span data-ttu-id="42445-110">Fase 1: Crear el entorno de pruebas y desarrollo de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="42445-110">Phase 1: Create your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="42445-111">Siga las instrucciones en el [entorno de desarrollo y prueba el Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="42445-111">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-customize-the-microsoft-intune-company-portal-app"></a><span data-ttu-id="42445-112">Fase 2: Personalizar la aplicación del portal de empresa de Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="42445-112">Phase 2: Customize the Microsoft Intune Company Portal app</span></span>

<span data-ttu-id="42445-113">Use estos pasos para personalizar la aplicación de portal de empresa de Microsoft Intune para su compañía ficticia:</span><span class="sxs-lookup"><span data-stu-id="42445-113">Use these steps to customize the Microsoft Intune Company Portal app for your fictional company:</span></span>
  
1. <span data-ttu-id="42445-114">En una nueva ficha, abra la consola de administración de Microsoft Intune ([https://manage.microsoft.com](https://manage.microsoft.com)).</span><span class="sxs-lookup"><span data-stu-id="42445-114">On a new tab, open the Microsoft Intune administration console ([https://manage.microsoft.com](https://manage.microsoft.com)).</span></span>
    
2. <span data-ttu-id="42445-115">Haga clic en **Administrador** del panel de exploración y, a continuación, haga clic en **Administración de dispositivos móviles** en el panel de **administración** .</span><span class="sxs-lookup"><span data-stu-id="42445-115">Click **Admin** in the navigation pane, and then click **Mobile Device Management** in the **Administration** pane.</span></span>
    
3. <span data-ttu-id="42445-p103">En la lista **tareas** , seleccione **Establecer órgano de gestión de dispositivos móviles**. Asegúrese de que está establecido para **Microsoft Intune**.</span><span class="sxs-lookup"><span data-stu-id="42445-p103">In the **Tasks** list, select **Set Mobile Device Management Authority**. Ensure that it is set to **Microsoft Intune**.</span></span>
    
4. <span data-ttu-id="42445-118">En el panel de **administración** , haga clic en **Portal de la empresa**.</span><span class="sxs-lookup"><span data-stu-id="42445-118">In the **Administration** pane, click **Company Portal**.</span></span>
    
5. <span data-ttu-id="42445-119">En el panel de **Portal de empresa** , configure las siguientes opciones:</span><span class="sxs-lookup"><span data-stu-id="42445-119">In the **Company Portal** pane, configure the following settings:</span></span>
    
  - <span data-ttu-id="42445-120">Nombre de la empresa: \<nombre de su compañía ficticia ></span><span class="sxs-lookup"><span data-stu-id="42445-120">Company name: \<your fictional company name></span></span>
    
  - <span data-ttu-id="42445-121">Nombre contacto del departamento de TI: **usuario5**</span><span class="sxs-lookup"><span data-stu-id="42445-121">IT department contact name: **User5**</span></span>
    
  - <span data-ttu-id="42445-122">Número de teléfono del departamento de TI: **555-1234**</span><span class="sxs-lookup"><span data-stu-id="42445-122">IT department phone number: **555-1234**</span></span>
    
  - <span data-ttu-id="42445-123">Dirección de correo electrónico del departamento de TI: **usuario5 @**\<nombre de la organización ficticia > **. onmicrosoft.com** (la dirección de correo electrónico de la cuenta de usuario5)</span><span class="sxs-lookup"><span data-stu-id="42445-123">IT department e-mail address: **User5@**\<fictional organization name> **.onmicrosoft.com** (the email address of the User5 account)</span></span>
    
6. <span data-ttu-id="42445-124">En **personalización**, seleccione **verde** en los **colores del tema**.</span><span class="sxs-lookup"><span data-stu-id="42445-124">In **Customization**, select **Green** in **Theme color**.</span></span>
    
7. <span data-ttu-id="42445-125">Haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="42445-125">Click **Save**.</span></span>
    
<span data-ttu-id="42445-126">A continuación, instalará la aplicación del portal de empresa de Microsoft Intune e inscribirá un dispositivo iOS o Android. Además, probará la funcionalidad de administración básica de la consola de administración de Microsoft Intune.</span><span class="sxs-lookup"><span data-stu-id="42445-126">Next, you will install the Microsoft Intune Company Portal app and enroll an iOS or Android device, and then test basic management functionality from the Microsoft Intune administration console.</span></span>
  
## <a name="phase-3-for-ios-devices-only-enroll-and-manage-an-ios-device"></a><span data-ttu-id="42445-127">Fase 3 (solo para dispositivos iOS): Inscribir y administrar un dispositivo iOS</span><span class="sxs-lookup"><span data-stu-id="42445-127">Phase 3 (for iOS devices only): Enroll and manage an iOS device</span></span>

<span data-ttu-id="42445-128">Para inscribir un dispositivo iOS para su administración en Intune, necesita lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="42445-128">To enroll an iOS device for management by Intune, you will need the following:</span></span>
  
- <span data-ttu-id="42445-129">Un dispositivo iOS como un iPhone o iPad de Apple.</span><span class="sxs-lookup"><span data-stu-id="42445-129">An iOS device such as an Apple iPad or iPhone.</span></span>
    
- <span data-ttu-id="42445-130">Conocimiento de la contraseña del dispositivo iOS.</span><span class="sxs-lookup"><span data-stu-id="42445-130">Knowledge of the iOS device's passcode.</span></span>
    
- <span data-ttu-id="42445-p104">Un ID de Apple (nombre de cuenta y contraseña). Si ya tiene uno, vaya a la [página Web de ID de Apple](https://appleid.apple.com/#!&amp;page=signin) y haga clic en **crear su ID de Apple**. Crear un ID de Apple correspondiente a la cuenta de administrador global de la suscripción de Office 365. Registrar su nuevo nombre de cuenta de Apple ID y la contraseña en un lugar seguro.</span><span class="sxs-lookup"><span data-stu-id="42445-p104">An Apple ID (an account name and password). If you do not already have one, go to the [Apple ID website](https://appleid.apple.com/#!&amp;page=signin) and click **Create your Apple ID**. Create an Apple ID corresponding to the global administrator account of your Office 365 subscription. Record your new Apple ID account name and password in a secure location.</span></span>
    
<span data-ttu-id="42445-p105">Se requiere un certificado de Apple Push Notification Service (APN) para que Intune administre dispositivos iOS y Mac. Una vez que el certificado se haya agregado a Intune, los usuarios podrán instalar la aplicación del portal de empresa de Microsoft Intune para inscribir sus dispositivos o el administrador podrá configurar la administración de dispositivos iOS de propiedad corporativa.</span><span class="sxs-lookup"><span data-stu-id="42445-p105">An Apple Push Notification service (APNs) certificate is required for Intune to manage iOS and Mac devices. Once the certificate is added to Intune, users can install the Microsoft Intune Company Portal app to enroll their devices or the administrator can set up corporate-owned iOS device management.</span></span>
  
<span data-ttu-id="42445-p106">Es necesario un archivo de solicitud de firma de certificado para solicitar un certificado de relación de confianza desde el Portal de certificados push de Apple. Para obtener un archivo de solicitud de firma de certificado:</span><span class="sxs-lookup"><span data-stu-id="42445-p106">You need a certificate signing request file to request a trust relationship certificate from the Apple Push Certificates Portal. To get a certificate signing request file:</span></span>
  
1. <span data-ttu-id="42445-139">En la consola de administración Microsoft Intune, haga clic en **Administrador** del panel de exploración.</span><span class="sxs-lookup"><span data-stu-id="42445-139">In the Microsoft Intune administration console, click **Admin** in the navigation pane.</span></span>
    
    <span data-ttu-id="42445-140">En el panel de **administración** , abra **Mobile Device Management > iOS y Mac OS X**y, a continuación, haga clic en **cargar un certificado APN** en **tareas**.</span><span class="sxs-lookup"><span data-stu-id="42445-140">In the **Administration** pane, open **Mobile Device Management > iOS and Mac OS X**, and then click **Upload an APNs Certificate** in **Tasks**.</span></span> 
    
2. <span data-ttu-id="42445-p107">En el panel **cargar un certificado APN** , haga clic en **Descargar la solicitud de certificado de APN**. Guardar el certificado de firma de archivo de solicitud (.csr) localmente con el nombre de **desarrollo y pruebas**.</span><span class="sxs-lookup"><span data-stu-id="42445-p107">In the **Upload an APNs Certificate** pane, click **Download the APNs certificate request**. Save the certificate signing request (.csr) file locally with the name **dev-test**.</span></span>
    
<span data-ttu-id="42445-143">Para obtener un certificado de Apple Push Notification Service:</span><span class="sxs-lookup"><span data-stu-id="42445-143">To get an Apple Push Notification service certificate:</span></span>
  
1. <span data-ttu-id="42445-144">Abrir una nueva pestaña, vaya al [Portal de certificados Push de Apple](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2)e iniciar sesión con su ID de Apple.</span><span class="sxs-lookup"><span data-stu-id="42445-144">Open a new tab, go to the [Apple Push Certificates Portal](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2), and sign in with your Apple ID.</span></span>
    
2. <span data-ttu-id="42445-145">En la página **Introducción** , haga clic en **crear un certificado**.</span><span class="sxs-lookup"><span data-stu-id="42445-145">On the **Get Started** page, click **Create a Certificate**.</span></span>
    
3. <span data-ttu-id="42445-146">En la página **Condiciones de uso** , seleccione **he leído y acepta estos términos y condiciones**y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="42445-146">On the **Terms of Use** page, select **I have read and agree to these terms and conditions**, and then click **Accept**.</span></span>
    
4. <span data-ttu-id="42445-p108">En la página **crear un certificado nuevo de inserción** , haga clic en **Examinar** y, a continuación, haga clic en **cargar** **dev test.csr** guardado el archivo en el procedimiento anterior. Cuando se le pida para abrir un archivo json, guárdelo en la misma carpeta donde está almacenado el archivo dev-test.csr.</span><span class="sxs-lookup"><span data-stu-id="42445-p108">On the **Create a New Push Certificate** page, click **Browse** and select the **dev-test.csr** file saved in the previous procedure, and then click **Upload**. When prompted to open a json file, save it to the same folder where the dev-test.csr file is stored.</span></span>
    
5. <span data-ttu-id="42445-149">Abra el [Portal certificados Push de Apple](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2) en una ficha diferente y para los **certificados para los servidores de otros fabricantes**, haga clic en **Descargar**.</span><span class="sxs-lookup"><span data-stu-id="42445-149">Open the [Apple Push Certificates Portal](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2) in a different tab and for **Certificates for Third-Party Servers**, click **Download**.</span></span>
    
6. <span data-ttu-id="42445-p109">Cuando se le pida para abrir un archivo .pem, guárdelo con el nombre **test.pem de desarrollo** en la misma carpeta donde está almacenado el archivo dev-test.csr. Éste es el certificado de APN.</span><span class="sxs-lookup"><span data-stu-id="42445-p109">When prompted to open a .pem file, save it with the name **dev-test.pem** to the same folder where the dev-test.csr file is stored. This is your APNs certificate.</span></span>
    
<span data-ttu-id="42445-152">Para cargar el certificado de APNs en Intune:</span><span class="sxs-lookup"><span data-stu-id="42445-152">To upload the APNs certificate into Intune:</span></span>
  
1. <span data-ttu-id="42445-153">En la ficha de la consola de administración de Microsoft Intune, en la página **cargar un certificado APN** , haga clic en **cargar el certificado APN**.</span><span class="sxs-lookup"><span data-stu-id="42445-153">On the Microsoft Intune administration console tab, on the **Upload an APNs Certificate** page, click **Upload the APNs certificate**.</span></span>
    
2. <span data-ttu-id="42445-154">Haga clic en **Examinar** y especifique el archivo **dev-test.pem** .</span><span class="sxs-lookup"><span data-stu-id="42445-154">Click **Browse** and specify the **dev-test.pem** file.</span></span>
    
3. <span data-ttu-id="42445-p110">Haga clic en **Abrir**, escriba su nombre de cuenta de ID de Apple y, a continuación, haga clic en **cargar**. Debería ver un mensaje **listo para la inscripción** en la página **iOS y X MaxOS configuración de dispositivo móvil** .</span><span class="sxs-lookup"><span data-stu-id="42445-p110">Click **Open**, type your Apple ID account name, and then click **Upload**. You should see a **Ready for enrollment** message on the **iOS and MaxOS X Mobile Device Management Setup** page.</span></span>
    
<span data-ttu-id="42445-157">Con el certificado de APNs instalado, Intune ahora puede inscribir y administrar dispositivos iOS insertando directivas en los dispositivos móviles inscritos.</span><span class="sxs-lookup"><span data-stu-id="42445-157">With the APNs certificate installed, Intune can now enroll and manage iOS devices by pushing policy to enrolled mobile devices.</span></span>
  
<span data-ttu-id="42445-158">Para descargar la aplicación del portal de empresa de Microsoft Intune e inscribir el dispositivo iOS:</span><span class="sxs-lookup"><span data-stu-id="42445-158">To download the Microsoft Intune Company portal app and enroll the iOS device:</span></span>
  
1. <span data-ttu-id="42445-159">En el dispositivo iOS, inicie sesión con su Apple ID.</span><span class="sxs-lookup"><span data-stu-id="42445-159">From your iOS device, sign in with your Apple ID.</span></span>
    
2. <span data-ttu-id="42445-160">Abra la aplicación **Tienda de Apple** .</span><span class="sxs-lookup"><span data-stu-id="42445-160">Open the **Apple Store** app.</span></span>
    
3. <span data-ttu-id="42445-161">Escriba **intune** en el cuadro de búsqueda y en el **Portal de empresa de Microsoft Intune**, entonces **obtener**y, a continuación, **instalar**.</span><span class="sxs-lookup"><span data-stu-id="42445-161">Type **intune** in the search box and tap **Microsoft Intune Company Portal**, then **Get**, and then **Install**.</span></span>
    
4. <span data-ttu-id="42445-162">Después de que instale, puntee en **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="42445-162">After it installs, tap **Open**.</span></span>
    
5. <span data-ttu-id="42445-163">En la pantalla de **Portal de empresa Intune** , inicie sesión con su cuenta de administrador global de Office 365.</span><span class="sxs-lookup"><span data-stu-id="42445-163">On the **Intune Company Portal** screen, sign in with your Office 365 global administrator account.</span></span>
    
6. <span data-ttu-id="42445-164">En la pantalla de **Configuración de acceso de la compañía** , puntee en **Iniciar**y, a continuación, puntee dos veces en **continuar** .</span><span class="sxs-lookup"><span data-stu-id="42445-164">On the **Company Access Setup** screen, tap **Begin**, and then tap **Continue** twice.</span></span>
    
7. <span data-ttu-id="42445-165">En la **lo que viene a continuación?** de la pantalla, puntee en **Enroll**.</span><span class="sxs-lookup"><span data-stu-id="42445-165">On the **What comes next?** screen, tap **Enroll**.</span></span>
    
8. <span data-ttu-id="42445-166">En la **Administrador del dispositivo Activate?** de la pantalla, puntee en **Activar**.</span><span class="sxs-lookup"><span data-stu-id="42445-166">On the **Activate device administrator?** screen, tap **Activate**.</span></span>
    
9. <span data-ttu-id="42445-167">En la pantalla de **Perfil de administración** , puntee en **instalar**.</span><span class="sxs-lookup"><span data-stu-id="42445-167">On the **Management Profile** screen, tap **Install**.</span></span>
    
10. <span data-ttu-id="42445-168">En **Introducir contraseña**, escriba la contraseña del dispositivo iOS.</span><span class="sxs-lookup"><span data-stu-id="42445-168">In **Enter Passcode**, type your iOS device passcode.</span></span>
    
11. <span data-ttu-id="42445-169">En la pantalla **lo que viene a continuación** , puntee en **Enroll**.</span><span class="sxs-lookup"><span data-stu-id="42445-169">On the **What comes next** screen, tap **Enroll**.</span></span>
    
12. <span data-ttu-id="42445-170">En **Instalar perfil**, puntee en **instalar**.</span><span class="sxs-lookup"><span data-stu-id="42445-170">In **Install Profile**, tap **Install**.</span></span>
    
13. <span data-ttu-id="42445-171">En la página de **Advertencia** , puntee en **instalar**.</span><span class="sxs-lookup"><span data-stu-id="42445-171">On the **Warning** page, tap **Install**.</span></span>
    
14. <span data-ttu-id="42445-172">En la **Administración remota**, puntee en **Confiar**.</span><span class="sxs-lookup"><span data-stu-id="42445-172">In **Remote Management**, tap **Trust**.</span></span>
    
15. <span data-ttu-id="42445-173">Puntee en **hecho** para completar el proceso de inscripción.</span><span class="sxs-lookup"><span data-stu-id="42445-173">Tap **Done** to complete the enrollment process.</span></span>
    
16. <span data-ttu-id="42445-174">Cuando se le pida para **Abrir esta página en "Portal Comp"?**, puntee en **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="42445-174">When prompted to **Open this page in "Comp Portal"?**, tap **Open**.</span></span>
    
17. <span data-ttu-id="42445-175">En la pantalla de **Configuración de acceso de la compañía** , puntee en **Iniciar**y, a continuación, en **hecho**.</span><span class="sxs-lookup"><span data-stu-id="42445-175">On the **Company Access Setup** screen, tap **Begin**, and then tap **Done**.</span></span>
    
18. <span data-ttu-id="42445-176">En la pantalla principal de la aplicación del portal de empresa de Microsoft Intune, debería ver:</span><span class="sxs-lookup"><span data-stu-id="42445-176">On the main screen of the Microsoft Intune Company Portal app, you should see:</span></span>
    
  - <span data-ttu-id="42445-177">Un banner verde.</span><span class="sxs-lookup"><span data-stu-id="42445-177">A green banner.</span></span>
    
  - <span data-ttu-id="42445-178">El nombre de la compañía ficticia en la esquina superior izquierda.</span><span class="sxs-lookup"><span data-stu-id="42445-178">Your fictional company name in the upper left.</span></span>
    
  - <span data-ttu-id="42445-179">El nombre del dispositivo iOS aparece en **Mis dispositivos**.</span><span class="sxs-lookup"><span data-stu-id="42445-179">Your iOS device name listed in **My Devices**.</span></span>
    
  - <span data-ttu-id="42445-180">En la sección de **asistencia técnica** , el **Nombre del contacto** del **usuario5** con el número de teléfono **555-1234** y un botón de **contacto por correo electrónico** .</span><span class="sxs-lookup"><span data-stu-id="42445-180">In the **Helpdesk** section, the **Contact Name** of **User5** with the phone number of **555-1234** and a **Contact by email** button.</span></span>
    
<span data-ttu-id="42445-p111">Microsoft Intune proporciona capacidades de restablecimiento de código de acceso y bloqueo remoto. Si alguien pierde su dispositivo, puede bloquearlo de forma remota. Si alguien olvida su código de acceso, puede eliminar el código de forma remota.</span><span class="sxs-lookup"><span data-stu-id="42445-p111">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can remove the passcode remotely.</span></span>
  
<span data-ttu-id="42445-184">Para bloquear de forma remota un dispositivo iOS:</span><span class="sxs-lookup"><span data-stu-id="42445-184">To lock an iOS device remotely:</span></span>
  
1. <span data-ttu-id="42445-185">Desde el equipo de administración, en la ficha de consola de administración Microsoft Intune del explorador, haga clic en **grupos** en la exploración de la izquierda.</span><span class="sxs-lookup"><span data-stu-id="42445-185">From your administration computer, on the Microsoft Intune administration console tab of your browser, click **Groups** in the left navigation.</span></span>
    
2. <span data-ttu-id="42445-186">En el panel de **grupos** , abra **todos los dispositivos > dispositivos móviles todos > todos los dispositivos administrados de Direct**.</span><span class="sxs-lookup"><span data-stu-id="42445-186">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
3. <span data-ttu-id="42445-187">En el panel de **Todos los dispositivos administrados de directa** , haga clic en la ficha **dispositivos** .</span><span class="sxs-lookup"><span data-stu-id="42445-187">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
4. <span data-ttu-id="42445-188">En la lista de dispositivos, haga clic en su dispositivo iOS. </span><span class="sxs-lookup"><span data-stu-id="42445-188">In the devices list, click your iOS device.</span></span> 
    
5. <span data-ttu-id="42445-189">En su dispositivo iOS, asegúrese de que está en la pantalla principal. </span><span class="sxs-lookup"><span data-stu-id="42445-189">From your iOS device, make sure it is at the main screen.</span></span> 
    
6. <span data-ttu-id="42445-p112">Desde el equipo de administración, en la barra de tareas, haga clic en **tareas remotas > bloqueo remoto**. Observe el dispositivo iOS mientras se cambia a la pantalla de bloqueo.</span><span class="sxs-lookup"><span data-stu-id="42445-p112">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. Watch your iOS device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="42445-192">Para eliminar el código de acceso:</span><span class="sxs-lookup"><span data-stu-id="42445-192">To remove the passcode:</span></span>
  
1. <span data-ttu-id="42445-193">Desde el equipo de administración, en el panel de **Todos los dispositivos administrados de directa** , haga clic en la ficha **dispositivos** .</span><span class="sxs-lookup"><span data-stu-id="42445-193">From your administration computer, in the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
2. <span data-ttu-id="42445-p113">En la lista, haga clic en el dispositivo iOS. En la barra de tareas, haga clic en **tareas remotas > Restablecer contraseña**. Espere un minuto.</span><span class="sxs-lookup"><span data-stu-id="42445-p113">In the list, click your iOS device. On the taskbar, click **Remote Tasks > Passcode Reset**. Wait for one minute.</span></span>
    
3. <span data-ttu-id="42445-p114">Desde el dispositivo iOS, desbloquéelo y observe que ya no es un código de acceso. Para cambiar la contraseña de nuevo, vaya a **configuración**y, a continuación, **código de acceso**.</span><span class="sxs-lookup"><span data-stu-id="42445-p114">From your iOS device, unlock it and notice that there is no longer a passcode. To change the passcode back, go into **Settings**, and then **Passcode**.</span></span>
    
## <a name="phase-3-for-android-devices-only-enroll-and-manage-an-android-device"></a><span data-ttu-id="42445-199">Fase 3 (solo para dispositivos Android): Inscribir y administrar un dispositivo Android</span><span class="sxs-lookup"><span data-stu-id="42445-199">Phase 3 (for Android devices only): Enroll and manage an Android device</span></span>

<span data-ttu-id="42445-200">Necesita lo siguiente para inscribir un dispositivo Android para su administración en Intune:</span><span class="sxs-lookup"><span data-stu-id="42445-200">You will need the following to enroll an Android device for management by Intune:</span></span>
  
- <span data-ttu-id="42445-201">Un dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="42445-201">An Android device.</span></span>
    
- <span data-ttu-id="42445-202">Conocimiento de la contraseña del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="42445-202">Knowledge of the device's passcode.</span></span>
    
<span data-ttu-id="42445-203">Para descargar la aplicación del portal de empresa de Intune e inscribir el dispositivo Android:</span><span class="sxs-lookup"><span data-stu-id="42445-203">To download the Intune Company portal app and enroll the Android device:</span></span>
  
1. <span data-ttu-id="42445-204">Desde tu dispositivo Android, vaya a la **Tienda de Google Play**y, a continuación, puntee en **Empezar**.</span><span class="sxs-lookup"><span data-stu-id="42445-204">From your Android device, go to the **Google Play Store**, and then tap **Get Started**.</span></span>
    
2. <span data-ttu-id="42445-205">Escriba **intune** en el cuadro Buscar y, a continuación, puntee en **intune portal de la compañía** en los resultados de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="42445-205">Type **intune** in the search box, and then tap **intune company portal** in the search results.</span></span>
    
3. <span data-ttu-id="42445-206">Puntee en el elemento de **Portal de empresa Intune** y, a continuación, en **instalar**.</span><span class="sxs-lookup"><span data-stu-id="42445-206">Tap the **Intune Company Portal** item, and then tap **Install**.</span></span>
    
4. <span data-ttu-id="42445-207">En la pantalla **para completar la instalación de cuenta** , puntee en **continuar**y, a continuación, **Omitir**.</span><span class="sxs-lookup"><span data-stu-id="42445-207">On the **For Complete account setup** screen, tap **Continue**, and then **Skip**.</span></span>
    
5. <span data-ttu-id="42445-p115">En el **Portal de la empresa Intune**, puntee en **Aceptar**. El instala la aplicación.</span><span class="sxs-lookup"><span data-stu-id="42445-p115">In **Intune Company Portal**, tap **Accept**. The app installs.</span></span>
    
6. <span data-ttu-id="42445-210">Puntee en **Abrir**y, a continuación, puntee en **iniciar sesión**.</span><span class="sxs-lookup"><span data-stu-id="42445-210">Tap **Open**, and then tap **Sign in**.</span></span>
    
7. <span data-ttu-id="42445-211">En la pantalla de **Portal de empresa Intune** , inicie sesión con su cuenta de administrador global de Office 365.</span><span class="sxs-lookup"><span data-stu-id="42445-211">On the **Intune Company Portal** screen, sign in with your Office 365 global administrator account.</span></span>
    
8. <span data-ttu-id="42445-212">En la pantalla de **Configuración de acceso de la compañía** , puntee dos veces **empezar**y, a continuación, en **continuar** .</span><span class="sxs-lookup"><span data-stu-id="42445-212">On the **Company Access Setup** screen, tap **Begin**, and then **Continue** twice.</span></span>
    
9. <span data-ttu-id="42445-213">En la **lo que viene a continuación?** de la pantalla, puntee en **Enroll**.</span><span class="sxs-lookup"><span data-stu-id="42445-213">On the **What comes next?** screen, tap **Enroll**.</span></span>
    
10. <span data-ttu-id="42445-214">En la **Administrador del dispositivo Activate?** de la pantalla, puntee en **Activate.**</span><span class="sxs-lookup"><span data-stu-id="42445-214">On the **Activate device administrator?** screen, tap **Activate.**</span></span>
    
11. <span data-ttu-id="42445-p116">En la pantalla de la **Política de privacidad** , seleccione **reconozco** y, a continuación, puntee en **Confirmar**. Espere a que el proceso de inscripción completar.</span><span class="sxs-lookup"><span data-stu-id="42445-p116">On the **Privacy Policy** screen, select **I acknowledge** and then tap **Confirm**. Wait for the enrollment process to complete.</span></span>
    
12. <span data-ttu-id="42445-217">En la pantalla de **Configuración de acceso de la compañía** , puntee en **continuar**y, a continuación, en **hecho**.</span><span class="sxs-lookup"><span data-stu-id="42445-217">In the **Company Access Setup** screen, tap **Continue**, and then tap **Done**.</span></span>
    
13. <span data-ttu-id="42445-218">En la pantalla principal de la aplicación del portal de empresa de Microsoft Intune, debería ver un banner de color verde y el nombre de su compañía ficticia en la parte superior izquierda.</span><span class="sxs-lookup"><span data-stu-id="42445-218">On the main screen of the Microsoft Intune Company Portal app, you should see a green banner and your fictional company name in the upper left.</span></span>
    
14. <span data-ttu-id="42445-p117">Puntee en **Mis dispositivos**. Debería ver el nombre del dispositivo Android en la lista.</span><span class="sxs-lookup"><span data-stu-id="42445-p117">Tap **My devices**. You should see your Android device name in the list.</span></span>
    
15. <span data-ttu-id="42445-p118">Puntee en **el contacto TI**. Debería ver el número de teléfono de **555-1234**, un botón de **contacto por correo electrónico** , y póngase en contacto con la TI de **usuario5**.</span><span class="sxs-lookup"><span data-stu-id="42445-p118">Tap **Contact IT**. You should see the phone number of **555-1234**, a **Contact by email** button, and the IT contact of **User5**.</span></span>
    
<span data-ttu-id="42445-p119">Microsoft Intune proporciona capacidades de restablecimiento de código de acceso y bloqueo remoto. Si alguien pierde su dispositivo, puede bloquearlo de forma remota. Si alguien olvida su código de acceso, puede restablecerlo de forma remota.</span><span class="sxs-lookup"><span data-stu-id="42445-p119">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can reset the passcode remotely.</span></span>
  
<span data-ttu-id="42445-226">Para bloquear de forma remota un dispositivo Android:</span><span class="sxs-lookup"><span data-stu-id="42445-226">To lock an Android device remotely:</span></span>
  
1. <span data-ttu-id="42445-227">Desde el equipo de administración, en la ficha de consola de administración Microsoft Intune del explorador, haga clic en **grupos** en la exploración de la izquierda.</span><span class="sxs-lookup"><span data-stu-id="42445-227">From your administration computer, on the Microsoft Intune administration console tab of your browser, click **Groups** in the left navigation.</span></span>
    
2. <span data-ttu-id="42445-228">En el panel de **grupos** , abra **todos los dispositivos > dispositivos móviles todos > todos los dispositivos administrados de Direct**.</span><span class="sxs-lookup"><span data-stu-id="42445-228">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
3. <span data-ttu-id="42445-229">En el panel de **Todos los dispositivos administrados de directa** , haga clic en la ficha **dispositivos** .</span><span class="sxs-lookup"><span data-stu-id="42445-229">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
4. <span data-ttu-id="42445-230">En la lista de dispositivos, haga clic en su dispositivo Android. </span><span class="sxs-lookup"><span data-stu-id="42445-230">In the devices list, click your Android device.</span></span> 
    
5. <span data-ttu-id="42445-231">En su dispositivo Android, asegúrese de que está en la pantalla principal. </span><span class="sxs-lookup"><span data-stu-id="42445-231">From your Android device, make sure it is at the main screen.</span></span> 
    
6. <span data-ttu-id="42445-p120">Desde el equipo de administración, en la barra de tareas, haga clic en **tareas remotas > bloqueo remoto**. Cuando se le pida, haga clic en **Sí**.</span><span class="sxs-lookup"><span data-stu-id="42445-p120">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. When prompted, click **Yes**.</span></span>
    
7. <span data-ttu-id="42445-234">Observe su dispositivo Android mientras cambia a la pantalla de bloqueo.</span><span class="sxs-lookup"><span data-stu-id="42445-234">Watch your Android device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="42445-235">Cuando se restablece la contraseña para los dispositivos Android, el portal de administración Intune genera y configura una contraseña segura.</span><span class="sxs-lookup"><span data-stu-id="42445-235">When you reset the passcode for Android devices, the Intune administration portal generates and configures a strong passcode.</span></span>
  
<span data-ttu-id="42445-236">Para restablecer el código de acceso de forma remota:</span><span class="sxs-lookup"><span data-stu-id="42445-236">To reset the passcode remotely:</span></span>
  
1. <span data-ttu-id="42445-237">Desde el equipo de administración, en la ficha de consola de administración Microsoft Intune del explorador, en el panel de **Todos los dispositivos administrados de directa** , haga clic en el dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="42445-237">From your administration computer, on the Microsoft Intune administration console tab of your browser, in the **All Direct Managed Devices** pane, click your Android device.</span></span>
    
2. <span data-ttu-id="42445-238">En la barra de tareas, haga clic en **tareas remotas > Restablecer contraseña**.</span><span class="sxs-lookup"><span data-stu-id="42445-238">On the taskbar, click **Remote Tasks > Passcode Reset**.</span></span>
    
3. <span data-ttu-id="42445-p121">En la **tarea remota: restablecer contraseña** pregunta, haga clic en **Sí**. Espere un minuto.</span><span class="sxs-lookup"><span data-stu-id="42445-p121">On the **Remote Task: Passcode Reset** prompt, click **Yes**. Wait for one minute.</span></span>
    
4. <span data-ttu-id="42445-241">En el panel de **Todos los dispositivos administrados de directa** , haga clic en **Ver propiedades**.</span><span class="sxs-lookup"><span data-stu-id="42445-241">In the **All Direct Managed Devices** pane, click **View Properties**.</span></span>
    
5. <span data-ttu-id="42445-242">Bajo **Restablecer contraseña**, tenga en cuenta la nueva contraseña.</span><span class="sxs-lookup"><span data-stu-id="42445-242">Under **Passcode Reset**, note the new passcode.</span></span>
    
6. <span data-ttu-id="42445-243">En su dispositivo Android, introduzca el nuevo código de acceso en la pantalla de bloqueo. </span><span class="sxs-lookup"><span data-stu-id="42445-243">From your Android device, enter the new passcode from the lockout screen.</span></span> 
    
7. <span data-ttu-id="42445-244">Para cambiar la contraseña de nuevo, vaya a **configuración**, puntee en el **dispositivo**, puntee en la **pantalla de bloqueo**, escriba la nueva contraseña, puntee en **bloqueo de pantalla**y, a continuación, su elección para el código de acceso.</span><span class="sxs-lookup"><span data-stu-id="42445-244">To change the passcode back, go into **Settings**, tap **Device**, tap **Lock screen**, enter the new passcode again, tap **Screen lock**, and then your choice for the passcode.</span></span>
    
> [!TIP]
> <span data-ttu-id="42445-245">Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual de todos los artículos en la pila de la Guía del entorno de pruebas de One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="42445-245">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="42445-246">Consulte también</span><span class="sxs-lookup"><span data-stu-id="42445-246">See Also</span></span>

[<span data-ttu-id="42445-247">El entorno de pruebas y desarrollo empresarial de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="42445-247">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="42445-248">Directivas MAM para su entorno de pruebas y desarrollo empresarial de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="42445-248">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="42445-249">Guías de entorno de pruebas de adopción de la nube (TLG)</span><span class="sxs-lookup"><span data-stu-id="42445-249">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="42445-250">Movilidad en la empresa + seguridad (EMS)</span><span class="sxs-lookup"><span data-stu-id="42445-250">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


