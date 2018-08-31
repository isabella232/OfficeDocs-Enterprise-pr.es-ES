---
title: Autenticación multifactor para el entorno de desarrollo y pruebas de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/22/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: e2b354b9-7f18-4da0-9107-6245eae0f33f
description: 'Resumen: configure la autenticación multifactor mediante mensajes de texto enviados a un smartphone en un entorno de desarrollo y pruebas de Office 365.'
ms.openlocfilehash: 12458e2dd41518deb0b540e809a08c4df865a3df
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915665"
---
# <a name="multi-factor-authentication-for-your-office-365-devtest-environment"></a><span data-ttu-id="f52fc-103">Autenticación multifactor para el entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="f52fc-103">Multi-factor authentication for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="f52fc-104">**Resumen:** configure la autenticación multifactor mediante mensajes de texto enviados a un smartphone en un entorno de desarrollo y pruebas de Office 365.</span><span class="sxs-lookup"><span data-stu-id="f52fc-104">**Summary:** Configure multi-factor authentication using text messages sent to a smart phone in an Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="f52fc-p101">Si quiere obtener un nivel adicional de seguridad para iniciar sesión en su suscripción de Office 365, puede habilitar la autenticación multifactor de Azure, que requiere algo más que el nombre de usuario y una contraseña para comprobar una cuenta. Con la autenticación multifactor para Office 365, los usuarios deben confirmar una llamada telefónica, escribir un código de comprobación enviado en un mensaje de texto o especificar una contraseña de aplicación en su smartphone tras introducir correctamente la contraseña. Pueden iniciar sesión solo después de que se haya cumplido este segundo factor de autenticación. </span><span class="sxs-lookup"><span data-stu-id="f52fc-p101">For an additional level of security for signing in to your Office 365 subscription, you can enable Azure multi-factor authentication, which requires more than just a username and password to verify an account. With multi-factor authentication for Office 365, users are required to acknowledge a phone call, type a verification code sent in a text message, or specify an app password on their smart phones after correctly entering their passwords. They can sign in only after this second authentication factor has been satisfied.</span></span> 
  
<span data-ttu-id="f52fc-108">En este artículo, se describe cómo habilitar y probar la autenticación basada en mensajes de texto para una cuenta específica de Office 365.</span><span class="sxs-lookup"><span data-stu-id="f52fc-108">This article describes how to enable and test text message-based authentication for a specific Office 365 account.</span></span>
  
<span data-ttu-id="f52fc-109">Existen dos fases para configurar la autenticación multifactor para Office 365 en un entorno de desarrollo y prueba:</span><span class="sxs-lookup"><span data-stu-id="f52fc-109">There are two phases to setting up multi-factor authentication for Office 365 in a dev/test environment:</span></span>
  
1. <span data-ttu-id="f52fc-110">Crear el entorno de desarrollo y pruebas de Office 365.</span><span class="sxs-lookup"><span data-stu-id="f52fc-110">Create the Office 365 dev/test environment.</span></span>
    
2. <span data-ttu-id="f52fc-111">Habilitar y probar la autenticación multifactor para la cuenta Usuario 2.</span><span class="sxs-lookup"><span data-stu-id="f52fc-111">Enable and test multi-factor authentication for the User 2 account.</span></span>
    
> [!TIP]
> <span data-ttu-id="f52fc-112">Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual de todos los artículos en la pila de la Guía del entorno de pruebas de One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="f52fc-112">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="f52fc-113">Fase 1: Crear un entorno de desarrollo y pruebas ligero o de una empresa simulada de Office 365</span><span class="sxs-lookup"><span data-stu-id="f52fc-113">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="f52fc-114">Si desea probar la autenticación multifactor en una forma sencilla con los requisitos mínimos, siga las instrucciones que aparecen en las fases 2 y 3 del [entorno de desarrollo y prueba de Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="f52fc-114">If you just want to test multi-factor authentication in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="f52fc-115">Si desea probar la autenticación multifactor en una empresa simulada, siga las instrucciones que aparecen en la [sincronización de directorios para el entorno de desarrollo y prueba de Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="f52fc-115">If you want to test multi-factor authentication in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="f52fc-p102">Probar la autenticación multifactor no requiere el entorno de desarrollo y pruebas de una empresa simulada, que incluye una intranet simulada conectada a Internet y la sincronización de directorios para un bosque de Windows Server AD. Aquí se ofrece como opción para que pueda probar la autenticación multifactor y experimentar con ella en un entorno que representa una organización típica.</span><span class="sxs-lookup"><span data-stu-id="f52fc-p102">Testing multi-factor authentication does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test multi-factor authentication and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a><span data-ttu-id="f52fc-118">Fase 2: habilitar y probar la autenticación multifactor para la cuenta Usuario 2</span><span class="sxs-lookup"><span data-stu-id="f52fc-118">Phase 2: Enable and test multi-factor authentication for the User 2 account</span></span>

<span data-ttu-id="f52fc-119">Siga estos pasos para habilitar la autenticación multifactor para la cuenta Usuario 2:</span><span class="sxs-lookup"><span data-stu-id="f52fc-119">Enable multi-factor authentication for the User 2 account with these steps:</span></span>
  
1. <span data-ttu-id="f52fc-120">Abra una instancia independiente del explorador, vaya al portal de Office 365 ([https://portal.office.com](https://portal.office.com)) y, a continuación, inicie sesión en su suscripción de prueba de Office 365 con su cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="f52fc-120">Open a separate instance of your browser, go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)), and then sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="f52fc-121">En la página principal del portal, haga clic en **Administración**.</span><span class="sxs-lookup"><span data-stu-id="f52fc-121">From the main portal page, click **Admin**.</span></span>
    
3. <span data-ttu-id="f52fc-122">En el panel de navegación izquierdo, haga clic en **Usuarios > Usuarios activos**.</span><span class="sxs-lookup"><span data-stu-id="f52fc-122">In the left navigation, click **Users > Active users**.</span></span>
    
4. <span data-ttu-id="f52fc-123">En el panel Usuarios activos, haga clic en **Más > Setup Azure multi-factor auth** (Configurar la autenticación multifactor de Azure).</span><span class="sxs-lookup"><span data-stu-id="f52fc-123">In the Active users pane, click **More > Setup Azure multi-factor auth**.</span></span>
    
5. <span data-ttu-id="f52fc-124">En la lista, seleccione la cuenta de **usuario 2** .</span><span class="sxs-lookup"><span data-stu-id="f52fc-124">In the list, select the **User 2** account.</span></span>
    
6. <span data-ttu-id="f52fc-125">En la sección **Usuario 2**, en **Pasos rápidos**, haga clic en **Habilitar**.</span><span class="sxs-lookup"><span data-stu-id="f52fc-125">In the **User 2** section, under **Quick steps**, click **Enable**.</span></span>
    
7. <span data-ttu-id="f52fc-126">En el cuadro de diálogo **Acerca de la habilitación de autenticación multifactor**, haga clic en **Habilitar Multi-Factor Auth**.</span><span class="sxs-lookup"><span data-stu-id="f52fc-126">In the **About enabling multi-factor auth** dialog box, click **Enable multi-factor auth**.</span></span>
    
8. <span data-ttu-id="f52fc-127">En el cuadro de diálogo **Actualización correcta**, haga clic en **Cerrar**.</span><span class="sxs-lookup"><span data-stu-id="f52fc-127">In the **Update successful** dialog box, click **Close**.</span></span>
    
9. <span data-ttu-id="f52fc-128">En la pestaña **Página principal de Microsoft Office**, haga clic en el icono de cuenta de usuario en la esquina superior derecha y, después, en **Cerrar sesión**.</span><span class="sxs-lookup"><span data-stu-id="f52fc-128">On the **Microsoft Office Home** tab, click the user account icon in the upper right, and then click **Sign out**.</span></span>
    
10. <span data-ttu-id="f52fc-129">Cierre la instancia del explorador.</span><span class="sxs-lookup"><span data-stu-id="f52fc-129">Close your browser instance.</span></span>
    
<span data-ttu-id="f52fc-130">Complete la configuración de la cuenta Usuario 2 para usar un mensaje de texto con fines de validación y prueba mediante los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="f52fc-130">Complete the configuration for the User 2 account to use a text message for validation and test it with these steps:</span></span>
  
1. <span data-ttu-id="f52fc-131">Abra una nueva instancia del explorador.</span><span class="sxs-lookup"><span data-stu-id="f52fc-131">Open a new instance of your browser.</span></span>
    
2. <span data-ttu-id="f52fc-132">Vaya al portal de Office 365 ([https://portal.office.com](https://portal.office.com)) y el inicio de sesión con la cuenta de usuario 2 (user2 @\<nombre de la organización >. onmicrosoft.com) y la contraseña.</span><span class="sxs-lookup"><span data-stu-id="f52fc-132">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in with the User 2 account (user2@\<organization name>.onmicrosoft.com) and password.</span></span>
    
3. <span data-ttu-id="f52fc-p103">Después de iniciar sesión, se le pedirá que configure la cuenta para la validación de seguridad adicional. Haga clic en **Configurar ahora**.</span><span class="sxs-lookup"><span data-stu-id="f52fc-p103">After signing in, you are prompted to set up the account for additional security validation. Click **Set it up now**.</span></span>
    
4. <span data-ttu-id="f52fc-135">En la página **Comprobación de seguridad adicional**: </span><span class="sxs-lookup"><span data-stu-id="f52fc-135">On the **Additional security verification** page:</span></span>
    
  - <span data-ttu-id="f52fc-136">Seleccione el país o región.</span><span class="sxs-lookup"><span data-stu-id="f52fc-136">Select your country or region.</span></span>
    
  - <span data-ttu-id="f52fc-137">Escriba el número de teléfono del smartphone que va a recibir los mensajes de texto.</span><span class="sxs-lookup"><span data-stu-id="f52fc-137">Type phone number of the smart phone that will receive text messages.</span></span>
    
  - <span data-ttu-id="f52fc-138">en **método**, haga clic en **Enviarme un código por mensaje de texto**.</span><span class="sxs-lookup"><span data-stu-id="f52fc-138">in **Method**, click **Send me a code by text message**.</span></span>
    
5. <span data-ttu-id="f52fc-139">Haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="f52fc-139">Click **Next**.</span></span>
    
6. <span data-ttu-id="f52fc-140">Escriba el código de comprobación incluido en el mensaje de texto que ha recibido en el smartphone y, después, haga clic en **Comprobar**.</span><span class="sxs-lookup"><span data-stu-id="f52fc-140">Enter the verification code from the text message received on your smart phone, and then click **Verify**.</span></span>
    
7. <span data-ttu-id="f52fc-141">En la página **Step 3: Keep your existing applications** (Paso 3: conservar las aplicaciones existentes), guarde en una ubicación segura la contraseña de aplicación que se muestra para la cuenta Usuario 2 y, después, haga clic en **Listo**.</span><span class="sxs-lookup"><span data-stu-id="f52fc-141">On the **Step 3: Keep your existing applications** page, record the displayed app password for the User 2 account in a secure location, and then click **Done**.</span></span>
    
8. <span data-ttu-id="f52fc-p104">Si es la primera vez que inicia sesión con la cuenta Usuario 2, se le pedirá que cambie la contraseña. Escriba la contraseña original y la contraseña nueva dos veces y, después, haga clic en **Actualizar contraseña e iniciar sesión**. Anote la contraseña nueva en un lugar seguro.</span><span class="sxs-lookup"><span data-stu-id="f52fc-p104">If this is the first time you signed in with the User 2 account, you are prompted to change the password. Type the original password and a new password twice, and then click **Update password and sign in**. Record the new password in a secure location.</span></span>
    
    <span data-ttu-id="f52fc-145">Debería ver el portal de Office 365 para el usuario 2 en la ficha **Página principal de Microsoft Office** del explorador.</span><span class="sxs-lookup"><span data-stu-id="f52fc-145">You should see the Office 365 portal for User 2 on the **Microsoft Office Home** tab of your browser.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="f52fc-146">Vea también</span><span class="sxs-lookup"><span data-stu-id="f52fc-146">See Also</span></span>

[<span data-ttu-id="f52fc-147">Guías del laboratorio de pruebas de adopción de la nube (TLG)</span><span class="sxs-lookup"><span data-stu-id="f52fc-147">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="f52fc-148">Entorno de desarrollo y pruebas de la configuración básica</span><span class="sxs-lookup"><span data-stu-id="f52fc-148">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="f52fc-149">Entorno de desarrollo y prueba de Office 365</span><span class="sxs-lookup"><span data-stu-id="f52fc-149">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="f52fc-150">Adopción de la nube y soluciones híbridas</span><span class="sxs-lookup"><span data-stu-id="f52fc-150">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="f52fc-151">Planeación de la autenticación multifactor para las implementaciones de Office 365</span><span class="sxs-lookup"><span data-stu-id="f52fc-151">Plan for multi-factor authentication for Office 365 Deployments</span></span>](https://support.office.com/article/Plan-for-multi-factor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

