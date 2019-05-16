---
title: Protección contra amenazas avanzada en el entorno de desarrollo y pruebas de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
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
ms.assetid: 51019757-20ac-498c-b51e-cae6d41a8c08
description: 'Resumen: configure y demuestre la Protección contra amenazas avanzada de Office 365 en el entorno de desarrollo y pruebas de Office 365.'
ms.openlocfilehash: 7063b56762711fdb06c0c879d74b783c0137b550
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068306"
---
# <a name="advanced-threat-protection-for-your-office-365-devtest-environment"></a><span data-ttu-id="4405c-103">Protección contra amenazas avanzada en el entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="4405c-103">Advanced Threat Protection for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="4405c-104">**Resumen:** configure y demuestre la Protección contra amenazas avanzada de Office 365 en el entorno de desarrollo y pruebas de Office 365.</span><span class="sxs-lookup"><span data-stu-id="4405c-104">**Summary:** Configure and demonstrate Office 365 Advanced Threat Protection in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="4405c-105">La Protección contra amenazas avanzada de Office 365 (ATP) es una característica de Exchange Online Protection (EOP) que ayuda a mantener el malware fuera de su correo electrónico.</span><span class="sxs-lookup"><span data-stu-id="4405c-105">Office 365 Advanced Threat Protection (ATP) is a feature of Exchange Online Protection (EOP) that helps keep malware out of your email.</span></span> <span data-ttu-id="4405c-106">Con ATP, se crean directivas en el centro de administración de Exchange (EAC) o &amp; en el centro de seguridad y cumplimiento que ayudan a los usuarios a acceder únicamente a vínculos o datos adjuntos en los correos electrónicos que se identifican como no malintencionados.</span><span class="sxs-lookup"><span data-stu-id="4405c-106">With ATP, you create policies in the Exchange admin center (EAC) or the Security &amp; Compliance center that help ensure your users access only links or attachments in emails that are identified as not malicious.</span></span> <span data-ttu-id="4405c-107">Para obtener más información, consulte [Protección contra amenazas avanzada para datos adjuntos seguros y vínculos seguros](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).</span><span class="sxs-lookup"><span data-stu-id="4405c-107">For more information, see [Advanced threat protection for safe attachments and safe links](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).</span></span>
  
<span data-ttu-id="4405c-108">Con las instrucciones de este artículo puede configurar y probar ATP en una suscripción de prueba de Office 365.</span><span class="sxs-lookup"><span data-stu-id="4405c-108">With the instructions in this article, you configure and test ATP in your Office 365 trial subscription.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="4405c-109">Fase 1: Crear un entorno de desarrollo y pruebas ligero o de una empresa simulada de Office 365</span><span class="sxs-lookup"><span data-stu-id="4405c-109">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="4405c-110">Si solo quiere probar ATP de manera ligera con los requisitos mínimos, siga las instrucciones indicadas en las fases 2 y 3 del [entorno de desarrollo y pruebas de Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="4405c-110">If you just want to test ATP in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="4405c-111">Si desea probar ATP en una empresa simulada, siga las instrucciones que se indican en [DirSync para el entorno de desarrollo y pruebas de Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="4405c-111">If you want to test ATP in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="4405c-112">La prueba de ATP no requiere el entorno de desarrollo y pruebas de una empresa simulada, que incluye una intranet simulada conectada a Internet y la sincronización de directorios para un bosque de servicios de dominio de Active Directory (AD DS).</span><span class="sxs-lookup"><span data-stu-id="4405c-112">Testing ATP does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for an Active Directory Domain Services (AD DS) forest.</span></span> <span data-ttu-id="4405c-113">Aquí se ofrece como opción para que pueda probar ATP y experimentar con ella en un entorno que representa una organización típica.</span><span class="sxs-lookup"><span data-stu-id="4405c-113">It is provided here as an option so that you can test ATP and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-the-default-email-delivery-behavior-of-office-365"></a><span data-ttu-id="4405c-114">Fase 2: demostrar el comportamiento de entrega de correo electrónico predeterminado de Office 365</span><span class="sxs-lookup"><span data-stu-id="4405c-114">Phase 2: Demonstrate the default email delivery behavior of Office 365</span></span>

<span data-ttu-id="4405c-115">En esta fase, se demuestra que antes de configurar directivas de ATP, se entrega correo electrónico potencialmente malintencionado a buzones de Office 365 sin filtrado ni mitigación.</span><span class="sxs-lookup"><span data-stu-id="4405c-115">In this phase, you demonstrate that before configuring ATP policies, potentially malicious email gets delivered to Office 365 mailboxes without screening or mitigation.</span></span>
  
1. <span data-ttu-id="4405c-116">Abra Internet Explorer e inicie sesión en la cuenta de Outlook que creó en la fase 2 del [entorno de desarrollo y pruebas de Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="4405c-116">Open Internet Explorer and sign in to the Outlook account you created in Phase 2 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
    
  - <span data-ttu-id="4405c-117">Si usa el entorno de desarrollo y pruebas ligero de Office 365, abra una sesión privada con Internet Explorer e inicie sesión desde el equipo local.</span><span class="sxs-lookup"><span data-stu-id="4405c-117">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="4405c-118">Si usa el entorno de desarrollo y pruebas de una empresa simulada de Office 365, use [Azure portal](https://portal.azure.com) para conectarse a la máquina virtual CLIENT1 y, a continuación, inicie sesión desde cliente1.</span><span class="sxs-lookup"><span data-stu-id="4405c-118">If you are using the simulated enterprise Office 365 dev/test environment, use the [Azure portal](https://portal.azure.com) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="4405c-119">Abra el Bloc de notas y escriba algún texto.</span><span class="sxs-lookup"><span data-stu-id="4405c-119">Run Notepad and enter some text.</span></span>
    
3. <span data-ttu-id="4405c-120">Guarde el archivo en la carpeta Documentos con el nombre **getKeys.js**.</span><span class="sxs-lookup"><span data-stu-id="4405c-120">Save the file to the Documents folder as **getKeys.js**.</span></span>
    
4. <span data-ttu-id="4405c-121">En la pestaña de Correo de Outlook de Internet Explorer, haga clic en **Nuevo**.</span><span class="sxs-lookup"><span data-stu-id="4405c-121">From the Outlook Mail tab of Internet Explorer, click **New**.</span></span>
    
5. <span data-ttu-id="4405c-122">En **Para**, escriba la dirección de correo electrónico del nombre de administrador global de Office 365 de su suscripción de prueba.</span><span class="sxs-lookup"><span data-stu-id="4405c-122">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
6. <span data-ttu-id="4405c-123">En el asunto, escriba **Sus nuevas claves**.</span><span class="sxs-lookup"><span data-stu-id="4405c-123">For the subject, type **Your new keys**.</span></span>
    
7. <span data-ttu-id="4405c-124">En el cuerpo, escriba **Aquí esta el archivo**.</span><span class="sxs-lookup"><span data-stu-id="4405c-124">In the body, type **Here is the file**.</span></span>
    
8. <span data-ttu-id="4405c-125">Haga clic en **Adjuntar**, haga doble clic en **getKeys.js** en la carpeta Documentos, haga clic en **Adjuntar como una copia** y después en **Enviar**.</span><span class="sxs-lookup"><span data-stu-id="4405c-125">Click **Attach**, double-click **getKeys.js** in the Documents folder, click **Attach as a copy**, and then click **Send**.</span></span>
    
9. <span data-ttu-id="4405c-126">Haga clic en **Nueva**.</span><span class="sxs-lookup"><span data-stu-id="4405c-126">Click **New**.</span></span>
    
10. <span data-ttu-id="4405c-127">En **Para**, escriba la dirección de correo electrónico del nombre de administrador global de Office 365 de su suscripción de prueba.</span><span class="sxs-lookup"><span data-stu-id="4405c-127">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
11. <span data-ttu-id="4405c-128">En el asunto, escriba **Nuevo sitio web de viajes**.</span><span class="sxs-lookup"><span data-stu-id="4405c-128">For the subject, type **New travel web site**.</span></span>
    
12. <span data-ttu-id="4405c-129">En el cuerpo, escriba **Alguien me ha reenviado este sitio**.</span><span class="sxs-lookup"><span data-stu-id="4405c-129">In the body, type **Someone forwarded me this site**.</span></span>
    
13. <span data-ttu-id="4405c-130">En el cuerpo, seleccione el texto **este sitio** y haga clic en el icono de hipervínculo en la barra de herramientas.</span><span class="sxs-lookup"><span data-stu-id="4405c-130">In the body, select the **this site** text and click the hyperlink icon in the toolbar.</span></span>
    
14. <span data-ttu-id="4405c-131">En **dirección URL**, **http://www.spamlink.contoso.com/** escriba, haga clic en **Aceptar**y, a continuación, haga clic en **Enviar**.</span><span class="sxs-lookup"><span data-stu-id="4405c-131">In **URL**, type **http://www.spamlink.contoso.com/**, click **OK**, and then click **Send**.</span></span>
    
15. <span data-ttu-id="4405c-132">Abra una instancia independiente de Internet Explorer en el modo de exploración privado, vaya al centro de administración de Microsoft[https://admin.microsoft.com](https://admin.microsoft.com)365 () e inicie sesión en su suscripción de prueba de Office 365 con su cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="4405c-132">Open a separate instance of Internet Explorer in private browsing mode, go to the Microsoft 365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com)), and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
16. <span data-ttu-id="4405c-133">Desde la página principal del portal, haga clic en el mosaico de aplicaciones y después en **Correo**.</span><span class="sxs-lookup"><span data-stu-id="4405c-133">From the main portal page, click the apps tile, and then click **Mail**.</span></span>
    
17. <span data-ttu-id="4405c-134">En la Bandeja de entrada, haga clic en el mensaje con el asunto **Sus nuevas claves**.</span><span class="sxs-lookup"><span data-stu-id="4405c-134">In the Inbox, click the message with the subject **Your new keys**.</span></span>
    
18. <span data-ttu-id="4405c-135">En la carpeta correo no deseado, haga clic en el mensaje con el asunto **nuevo sitio web de viajes**.</span><span class="sxs-lookup"><span data-stu-id="4405c-135">In the Junk Mail folder, click the message with the subject **New travel web site**.</span></span> <span data-ttu-id="4405c-136">En el mensaje, haga clic en el vínculo a **sitio** .</span><span class="sxs-lookup"><span data-stu-id="4405c-136">Within the message, click the **this site** link.</span></span> <span data-ttu-id="4405c-137">Debe ver un "vaya!</span><span class="sxs-lookup"><span data-stu-id="4405c-137">You should see a "Oops!</span></span> <span data-ttu-id="4405c-138">Internet Explorer no pudo encontrar spamlink.contoso.com. "</span><span class="sxs-lookup"><span data-stu-id="4405c-138">Internet Explorer could not find spamlink.contoso.com."</span></span> <span data-ttu-id="4405c-139">bloque.</span><span class="sxs-lookup"><span data-stu-id="4405c-139">page.</span></span> <span data-ttu-id="4405c-140">Este es el resultado correcto porque no hay ninguna página web en esa ubicación.</span><span class="sxs-lookup"><span data-stu-id="4405c-140">This is the correct result because there is no web page at that location.</span></span>
    
<span data-ttu-id="4405c-p104">Observe que ambos correos electrónicos potencialmente malintencionados se entregaron correctamente. El correo electrónico **Sus nuevas claves** podría contener software malintencionado no detectado y se permite al usuario hacer clic en el vínculo potencialmente malintencionado en el correo electrónico **Nuevo sitio web de viajes**.</span><span class="sxs-lookup"><span data-stu-id="4405c-p104">Notice that both of these potentially malicious emails were delivered successfully. The **Your new keys** email could contain undetected malware and the user was allowed to click the potentially malicious link in the **New travel web site** email.</span></span>
  
## <a name="phase-3-configure-safe-attachment-and-safe-links-policies-for-atp"></a><span data-ttu-id="4405c-143">Fase 3: Configurar directivas de vínculos y archivos adjuntos seguros de ATP</span><span class="sxs-lookup"><span data-stu-id="4405c-143">Phase 3: Configure safe attachment and safe links policies for ATP</span></span>

<span data-ttu-id="4405c-144">En esta fase, creará y configurará una directiva de datos adjuntos seguros para evitar que el correo electrónico con datos adjuntos potencialmente malintencionados se entregue y una directiva de vínculos seguros para evitar que los usuarios visiten direcciones URL potencialmente inseguras.</span><span class="sxs-lookup"><span data-stu-id="4405c-144">In this phase, you create and configure a safe attachment policy to prevent email with potentially malicious attachments from being delivered and a safe links policy to keep users from traveling to potentially unsafe URLs.</span></span>
  
1. <span data-ttu-id="4405c-145">En la pestaña **Inicio de Microsoft Office** de Internet Explorer, haga clic en el icono **Administración** .</span><span class="sxs-lookup"><span data-stu-id="4405c-145">On the **Microsoft Office Home** tab of Internet Explorer, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="4405c-146">En el panel de navegación izquierdo, haga clic en **Centros de administración** y después en **Exchange**.</span><span class="sxs-lookup"><span data-stu-id="4405c-146">In the left navigation, click **Admin centers**, and then **Exchange**.</span></span>
    
3. <span data-ttu-id="4405c-147">En el panel de navegación izquierdo de la pestaña Centro de administración de Exchange, haga clic en **amenazas avanzadas**.</span><span class="sxs-lookup"><span data-stu-id="4405c-147">In the left navigation of the Exchange admin center tab, click **advanced threats**.</span></span>
    
4. <span data-ttu-id="4405c-148">Haga clic en la pestaña **datos adjuntos seguros** y después en el signo más.</span><span class="sxs-lookup"><span data-stu-id="4405c-148">Click the **safe attachments** tab, and then click the plus sign.</span></span>
    
5. <span data-ttu-id="4405c-149">En la ventana **nueva Directiva de datos adjuntos seguros** , en **nombre**, escriba **Directiva de datos adjuntos seguros: bloquear**.</span><span class="sxs-lookup"><span data-stu-id="4405c-149">In the **new safe attachments policy** window, in **Name**, type **Safe Attachment Policy - Block**.</span></span>
    
6. <span data-ttu-id="4405c-150">Para la respuesta de malware desconocidos de **datos adjuntos seguros**, haga clic en **bloquear**.</span><span class="sxs-lookup"><span data-stu-id="4405c-150">For **Safe attachments unknown malware response**, click **Block**.</span></span>
    
7. <span data-ttu-id="4405c-151">En **Redirigir datos adjuntos al detectarlos**, haga clic en **Habilitar redirección** y escriba la dirección de correo electrónico de la cuenta de administrador global de Office 365.</span><span class="sxs-lookup"><span data-stu-id="4405c-151">For **Redirect attachment on detection**, click **Enable redirect** and type the email address of your Office 365 global administrator account.</span></span>
    
8. <span data-ttu-id="4405c-152">En **Aplicado a**, haga clic en la flecha abajo y después en **El dominio del destinatario es**.</span><span class="sxs-lookup"><span data-stu-id="4405c-152">For **Applied to**, click the down arrow, and then click **The recipient domain is**.</span></span> <span data-ttu-id="4405c-153">En la ventana, haga clic en el nombre de su organización (por ejemplo, contoso.onmicrosoft.com) y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="4405c-153">In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
9. <span data-ttu-id="4405c-154">Haga clic en \*\*Guardar \*\*.</span><span class="sxs-lookup"><span data-stu-id="4405c-154">Click **Save**.</span></span> <span data-ttu-id="4405c-155">Después de la actualización, debe ver el nuevo y habilitado **Directiva de datos adjuntos seguros: bloque**.</span><span class="sxs-lookup"><span data-stu-id="4405c-155">After the update, you should see the new and enabled **Safe Attachment Policy - Block**.</span></span>
    
10. <span data-ttu-id="4405c-156">Haga clic en la pestaña **Vínculos seguros** y después en el signo más.</span><span class="sxs-lookup"><span data-stu-id="4405c-156">Click the **safe links** tab, and then click the plus sign.</span></span>
    
11. <span data-ttu-id="4405c-157">En la ventana **Nueva directiva de vínculos seguros**, escriba **Directiva de vínculos seguros** en **Nombre**.</span><span class="sxs-lookup"><span data-stu-id="4405c-157">In the **new safe links policy** window, in **Name**, type **Safe Link Policy**.</span></span>
    
12. <span data-ttu-id="4405c-158">En **Seleccionar la acción para direcciones URL potencialmente malintencionadas desconocidas en mensajes**, haga clic en **Activado** y seleccione **No permitir a los usuarios hacer clic en la dirección URL original**.</span><span class="sxs-lookup"><span data-stu-id="4405c-158">For **Select the action for unknown potentially malicious URLs in messages**, click **On**, and then select **Do not allow users to click through to original URL**.</span></span>
    
13. <span data-ttu-id="4405c-159">En **Aplicado a**, haga clic en la flecha abajo y después en **El dominio del destinatario es**.</span><span class="sxs-lookup"><span data-stu-id="4405c-159">For **Applied to**, click the down arrow, and then click **The recipient domain is**.</span></span> <span data-ttu-id="4405c-160">En la ventana, haga clic en el nombre de su organización (por ejemplo, contoso.onmicrosoft.com) y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="4405c-160">In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
14. <span data-ttu-id="4405c-p108">Haga clic en **Guardar**. Debería ver la nueva y habilitada **Directiva de vínculos seguros**.</span><span class="sxs-lookup"><span data-stu-id="4405c-p108">Click **Save**. You should see the new and enabled **Safe Link Policy**.</span></span>
    
## <a name="phase-4-show-atp-in-action"></a><span data-ttu-id="4405c-163">Fase 4: Mostrar ATP en acción</span><span class="sxs-lookup"><span data-stu-id="4405c-163">Phase 4: Show ATP in action</span></span>

<span data-ttu-id="4405c-164">En esta fase, veremos cómo ATP se gestiona el correo electrónico malintencionado.</span><span class="sxs-lookup"><span data-stu-id="4405c-164">In this phase, you demonstrate how ATP deals with potentially malicious email.</span></span>
  
1. <span data-ttu-id="4405c-165">En la sesión de Internet Explorer que usó para enviar el correo electrónico en la fase 2, en el panel de navegación izquierdo, haga clic en **elementos enviados.**</span><span class="sxs-lookup"><span data-stu-id="4405c-165">From the instance of Internet Explorer that you used to send the email in Phase 2, in the left navigation, click **Sent Items.**</span></span>
    
2. <span data-ttu-id="4405c-166">Haga clic en el correo electrónico titulado **claves nuevas**, haga clic en el icono de flecha \*\*\*\* abajo y, a continuación, haga clic en reenviar.</span><span class="sxs-lookup"><span data-stu-id="4405c-166">Click the email titled **Your new keys**, click the down arrow icon, and then click **Forward**.</span></span>
    
3. <span data-ttu-id="4405c-167">En el nuevo mensaje, en **Para**, escriba la dirección de correo electrónico del nombre de administrador global de Office 365 de su suscripción de prueba y después haga clic en **Enviar**.</span><span class="sxs-lookup"><span data-stu-id="4405c-167">For the new message, in **To**, type the email address of the Office 365 global administrator name of your trial subscription, and then click **Send**.</span></span>
    
4. <span data-ttu-id="4405c-168">Haga clic en el correo electrónico titulado **nuevo sitio web de viajes**, haga clic en el icono de flecha abajo, haga clic en **responder a todos**y, a continuación, haga clic en **Enviar**.</span><span class="sxs-lookup"><span data-stu-id="4405c-168">Click the email titled **New travel web site**, click the down arrow icon, click **Reply all**, and then click **Send**.</span></span>
    
5. <span data-ttu-id="4405c-p109">Desde la instancia de Internet Explorer que usó para configurar directivas de ATP en la fase 3, haga clic en la pestaña Centro de administración de Exchange, en el mosaico de aplicaciones y en **Correo**. Verá dos nuevos mensajes de correo electrónico en la Bandeja de entrada:</span><span class="sxs-lookup"><span data-stu-id="4405c-p109">From the instance of Internet Explorer that you used to configure ATP policies in Phase 3, click the Exchange admin center tab, click the apps tile, and then click **Mail**. You should see two new email messages in the Inbox:</span></span>
    
  - <span data-ttu-id="4405c-171">Uno titulado **RV: Sus nuevas claves**</span><span class="sxs-lookup"><span data-stu-id="4405c-171">One titled **Fw: Your new keys**</span></span>
    
  - <span data-ttu-id="4405c-172">Uno titulado **RV: Nuevo sitio web de viajes**</span><span class="sxs-lookup"><span data-stu-id="4405c-172">One titled **Fw: New travel web site**</span></span>
    
6. <span data-ttu-id="4405c-173">Abra el mensaje de correo electrónico titulado **FW: nuevo sitio web de viajes** y haga clic en este vínculo de **sitio** .</span><span class="sxs-lookup"><span data-stu-id="4405c-173">Open the email message titled **Fw: New travel web site** and click the **this site** link.</span></span> <span data-ttu-id="4405c-174">Debería ver "este sitio web se ha clasificado como malintencionado".</span><span class="sxs-lookup"><span data-stu-id="4405c-174">You should see a "This website has been classified as malicious."</span></span> <span data-ttu-id="4405c-175">bloque.</span><span class="sxs-lookup"><span data-stu-id="4405c-175">page.</span></span> <span data-ttu-id="4405c-176">Esto demuestra que ATP está impidiendo el acceso al sitio Web potencialmente malintencionado.</span><span class="sxs-lookup"><span data-stu-id="4405c-176">This demonstrates that ATP is preventing you from accessing the potentially malicious web site.</span></span>
    
7. <span data-ttu-id="4405c-177">En la pestaña Centro de administración de Exchange de Internet Explorer, en el panel de exploración izquierdo, haga clic en **Flujo de correo**.</span><span class="sxs-lookup"><span data-stu-id="4405c-177">In the Exchange admin center tab of Internet Explorer, in the left navigation, click **mail flow**.</span></span>
    
8. <span data-ttu-id="4405c-178">Haga clic en la pestaña **Seguimiento de mensajes** y después en **Buscar**.</span><span class="sxs-lookup"><span data-stu-id="4405c-178">Click the **message trace** tab, and then click **search**.</span></span>
    
9. <span data-ttu-id="4405c-179">En la ventana **Resultados de seguimiento de mensajes**, haga doble clic en el mensaje con el asunto **Sus nuevas claves**.</span><span class="sxs-lookup"><span data-stu-id="4405c-179">In the **Message Trace Results** window, double-click the message with the subject **Your new keys**.</span></span> <span data-ttu-id="4405c-180">Este mensaje se entregó correctamente a la bandeja de entrada.</span><span class="sxs-lookup"><span data-stu-id="4405c-180">This message was successfully delivered to the Inbox.</span></span> <span data-ttu-id="4405c-181">Cierre esta ventana.</span><span class="sxs-lookup"><span data-stu-id="4405c-181">Close this window.</span></span>
    
10. <span data-ttu-id="4405c-182">Haga doble clic en el mensaje con el asunto **Nuevo sitio web de viajes**.</span><span class="sxs-lookup"><span data-stu-id="4405c-182">Double-click the message with the subject **New travel web site**.</span></span> <span data-ttu-id="4405c-183">Este mensaje se entregó correctamente a la bandeja de entrada.</span><span class="sxs-lookup"><span data-stu-id="4405c-183">This message was successfully delivered to the Inbox.</span></span> <span data-ttu-id="4405c-184">Cierre esta ventana.</span><span class="sxs-lookup"><span data-stu-id="4405c-184">Close this window.</span></span>
    
11. <span data-ttu-id="4405c-185">Haga doble clic en el mensaje con el asunto **RV: Sus nuevas claves**.</span><span class="sxs-lookup"><span data-stu-id="4405c-185">Double-click the message with the subject **Fw: Your new keys**.</span></span> <span data-ttu-id="4405c-186">Tenga en cuenta que ATP ha procesado este mensaje y, a continuación, se entregó en la bandeja de entrada.</span><span class="sxs-lookup"><span data-stu-id="4405c-186">Note how this message was processed by ATP and then delivered to the Inbox.</span></span> <span data-ttu-id="4405c-187">Cierre esta ventana.</span><span class="sxs-lookup"><span data-stu-id="4405c-187">Close this window.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="4405c-188">La finalidad de la Directiva de datos adjuntos seguros era comenzar el examen de los datos adjuntos de código malintencionado.</span><span class="sxs-lookup"><span data-stu-id="4405c-188">The purpose of the safe attachments policy was to begin scanning attachments for malicious code.</span></span> <span data-ttu-id="4405c-189">Se permitió el dato adjunto de getKeys. js porque no se determinó que era malintencionado.</span><span class="sxs-lookup"><span data-stu-id="4405c-189">The getKeys.js attachment was allowed because it was not determined to be malicious.</span></span> <span data-ttu-id="4405c-190">Este paso muestra que ATP llevó a cabo un análisis de los datos adjuntos.</span><span class="sxs-lookup"><span data-stu-id="4405c-190">This step shows that ATP did perform a scan of the attachment.</span></span> 
  
12. <span data-ttu-id="4405c-191">Haga doble clic en el mensaje con el asunto **RV: Nuevo sitio web de viajes**.</span><span class="sxs-lookup"><span data-stu-id="4405c-191">Double-click the message with the subject **Fw: New travel web site**.</span></span> <span data-ttu-id="4405c-192">Tenga en cuenta que este mensaje se entregó correctamente a la bandeja de entrada.</span><span class="sxs-lookup"><span data-stu-id="4405c-192">Note that this message was successfully delivered to the Inbox.</span></span>
    
<span data-ttu-id="4405c-193">Ahora puede usar este entorno para crear nuevas directivas y experimentar con ATP.</span><span class="sxs-lookup"><span data-stu-id="4405c-193">You can now use this environment to create new policies and experiment with ATP.</span></span>
  
> [!TIP]
> <span data-ttu-id="4405c-194">Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual de todos los artículos en la pila de la Guía del entorno de pruebas de Office 365.</span><span class="sxs-lookup"><span data-stu-id="4405c-194">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4405c-195">Vea también</span><span class="sxs-lookup"><span data-stu-id="4405c-195">See Also</span></span>

[<span data-ttu-id="4405c-196">Guías del laboratorio de pruebas de adopción de la nube (TLG)</span><span class="sxs-lookup"><span data-stu-id="4405c-196">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="4405c-197">Entorno de desarrollo y pruebas de la configuración básica</span><span class="sxs-lookup"><span data-stu-id="4405c-197">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="4405c-198">Entorno de desarrollo y prueba de Office 365</span><span class="sxs-lookup"><span data-stu-id="4405c-198">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="4405c-199">Sincronización de directorios (DirSync) para el entorno de desarrollo y prueba de Office 365</span><span class="sxs-lookup"><span data-stu-id="4405c-199">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="4405c-200">Seguridad de Cloud App para su entorno de desarrollo y prueba de Office 365</span><span class="sxs-lookup"><span data-stu-id="4405c-200">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="4405c-201">Adopción de la nube y soluciones híbridas</span><span class="sxs-lookup"><span data-stu-id="4405c-201">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md) 

[<span data-ttu-id="4405c-202">Protección contra amenazas avanzada para datos adjuntos seguros y vínculos seguros</span><span class="sxs-lookup"><span data-stu-id="4405c-202">Advanced threat protection for safe attachments and safe links</span></span>](https://support.office.com/article/Office-365-Advanced-Threat-Protection-E100FE7C-F2A1-4B7D-9E08-622330B83653)


