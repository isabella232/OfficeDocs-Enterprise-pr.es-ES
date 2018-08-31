---
title: Protección contra amenazas avanzada en el entorno de desarrollo y pruebas de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
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
ms.assetid: 51019757-20ac-498c-b51e-cae6d41a8c08
description: 'Resumen: configure y demuestre la Protección contra amenazas avanzada de Office 365 en el entorno de desarrollo y pruebas de Office 365.'
ms.openlocfilehash: 07411600db11c8eea825c0ef5b82ea1206d20e11
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914965"
---
# <a name="advanced-threat-protection-for-your-office-365-devtest-environment"></a><span data-ttu-id="c06b0-103">Protección contra amenazas avanzada en el entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="c06b0-103">Advanced Threat Protection for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="c06b0-104">**Resumen:** configure y demuestre la Protección contra amenazas avanzada de Office 365 en el entorno de desarrollo y pruebas de Office 365.</span><span class="sxs-lookup"><span data-stu-id="c06b0-104">**Summary:** Configure and demonstrate Office 365 Advanced Threat Protection in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="c06b0-p101">Protección de amenaza avanzada de Office 365 (ATP) es una característica de Exchange Online Protection (EOP) que ayuda a mantener el malware fuera de su correo electrónico. Con ATP, crear directivas en el centro de administración de Exchange (EAC) o la seguridad &amp; centro de cumplimiento que ayudan a garantizar que los usuarios tener acceso sólo vínculos o datos adjuntos en mensajes de correo electrónico que se identifican como no malintencionado. Para obtener más información, consulte [protección contra amenazas avanzadas para los datos adjuntos seguros y vínculos seguros](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).</span><span class="sxs-lookup"><span data-stu-id="c06b0-p101">Office 365 Advanced Threat Protection (ATP) is a feature of Exchange Online Protection (EOP) that helps keep malware out of your email. With ATP, you create policies in the Exchange admin center (EAC) or the Security &amp; Compliance center that help ensure your users access only links or attachments in emails that are identified as not malicious. For more information, see [Advanced threat protection for safe attachments and safe links](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).</span></span>
  
<span data-ttu-id="c06b0-108">Con las instrucciones de este artículo puede configurar y probar ATP en una suscripción de prueba de Office 365.</span><span class="sxs-lookup"><span data-stu-id="c06b0-108">With the instructions in this article, you configure and test ATP in your Office 365 trial subscription.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="c06b0-109">Fase 1: Crear un entorno de desarrollo y pruebas ligero o de una empresa simulada de Office 365</span><span class="sxs-lookup"><span data-stu-id="c06b0-109">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="c06b0-110">Si desea probar ATP en una forma sencilla con los requisitos mínimos, siga las instrucciones que aparecen en las fases 2 y 3 del [entorno de desarrollo y prueba de Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="c06b0-110">If you just want to test ATP in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="c06b0-111">Si desea probar ATP en una empresa simulada, siga las instrucciones que aparecen en la [sincronización de directorios para el entorno de desarrollo y prueba de Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="c06b0-111">If you want to test ATP in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="c06b0-p102">La realización de pruebas en ATP no requiere el entorno de desarrollo y pruebas de una empresa simulada, que incluye una intranet simulada conectada a Internet y la sincronización de directorios para un bosque de Windows Server AD. Aquí se ofrece como opción para que pueda probar ATP y experimentar con ella en un entorno que representa una organización típica.</span><span class="sxs-lookup"><span data-stu-id="c06b0-p102">Testing ATP does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test ATP and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-the-default-email-delivery-behavior-of-office-365"></a><span data-ttu-id="c06b0-114">Fase 2: Demostrar el comportamiento de entrega de correo electrónico predeterminado de Office 365</span><span class="sxs-lookup"><span data-stu-id="c06b0-114">Phase 2: Demonstrate the default email delivery behavior of Office 365</span></span>

<span data-ttu-id="c06b0-115">En esta fase, se demuestra que antes de configurar directivas de ATP, se entrega correo electrónico potencialmente malintencionado a buzones de Office 365 sin filtrado ni mitigación.</span><span class="sxs-lookup"><span data-stu-id="c06b0-115">In this phase, you demonstrate that before configuring ATP policies, potentially malicious email gets delivered to Office 365 mailboxes without screening or mitigation.</span></span>
  
1. <span data-ttu-id="c06b0-116">Abra Internet Explorer e inicie sesión la cuenta de Outlook que creó en la fase 2 del [entorno de desarrollo y prueba de Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="c06b0-116">Open Internet Explorer and sign in to the Outlook account you created in Phase 2 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
    
  - <span data-ttu-id="c06b0-117">Si usa el entorno de desarrollo y pruebas ligero de Office 365, abra una sesión privada con Internet Explorer e inicie sesión desde el equipo local.</span><span class="sxs-lookup"><span data-stu-id="c06b0-117">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="c06b0-118">Si está utilizando el entorno de desarrollo y prueba de Office 365 enterprise simulado, use el [portal de Azure](https://portal.azure.com) para conectarse a la máquina virtual CLIENT1 y, a continuación, iniciar sesión en desde CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="c06b0-118">If you are using the simulated enterprise Office 365 dev/test environment, use the [Azure portal](https://portal.azure.com) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="c06b0-119">Abra el Bloc de notas y escriba algún texto.</span><span class="sxs-lookup"><span data-stu-id="c06b0-119">Run Notepad and enter some text.</span></span>
    
3. <span data-ttu-id="c06b0-120">Guarde el archivo en la carpeta Documentos con el nombre **getKeys.js**.</span><span class="sxs-lookup"><span data-stu-id="c06b0-120">Save the file to the Documents folder as **getKeys.js**.</span></span>
    
4. <span data-ttu-id="c06b0-121">En la pestaña de Correo de Outlook de Internet Explorer, haga clic en **Nuevo**.</span><span class="sxs-lookup"><span data-stu-id="c06b0-121">From the Outlook Mail tab of Internet Explorer, click **New**.</span></span>
    
5. <span data-ttu-id="c06b0-122">En **Para**, escriba la dirección de correo electrónico del nombre de administrador global de Office 365 de su suscripción de prueba.</span><span class="sxs-lookup"><span data-stu-id="c06b0-122">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
6. <span data-ttu-id="c06b0-123">En el asunto, escriba **Sus nuevas claves**.</span><span class="sxs-lookup"><span data-stu-id="c06b0-123">For the subject, type **Your new keys**.</span></span>
    
7. <span data-ttu-id="c06b0-124">En el cuerpo, escriba **Aquí esta el archivo**.</span><span class="sxs-lookup"><span data-stu-id="c06b0-124">In the body, type **Here is the file**.</span></span>
    
8. <span data-ttu-id="c06b0-125">Haga clic en **Adjuntar**, haga doble clic en **getKeys.js** en la carpeta Documentos, haga clic en **Adjuntar como una copia** y después en **Enviar**.</span><span class="sxs-lookup"><span data-stu-id="c06b0-125">Click **Attach**, double-click **getKeys.js** in the Documents folder, click **Attach as a copy**, and then click **Send**.</span></span>
    
9. <span data-ttu-id="c06b0-126">Haga clic en **Nueva**.</span><span class="sxs-lookup"><span data-stu-id="c06b0-126">Click **New**.</span></span>
    
10. <span data-ttu-id="c06b0-127">En **Para**, escriba la dirección de correo electrónico del nombre de administrador global de Office 365 de su suscripción de prueba.</span><span class="sxs-lookup"><span data-stu-id="c06b0-127">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
11. <span data-ttu-id="c06b0-128">En el asunto, escriba **Nuevo sitio web de viajes**.</span><span class="sxs-lookup"><span data-stu-id="c06b0-128">For the subject, type **New travel web site**.</span></span>
    
12. <span data-ttu-id="c06b0-129">En el cuerpo, escriba **Alguien me ha reenviado este sitio**.</span><span class="sxs-lookup"><span data-stu-id="c06b0-129">In the body, type **Someone forwarded me this site**.</span></span>
    
13. <span data-ttu-id="c06b0-130">En el cuerpo, seleccione el texto **este sitio** y haga clic en el icono de hipervínculo en la barra de herramientas.</span><span class="sxs-lookup"><span data-stu-id="c06b0-130">In the body, select the **this site** text and click the hyperlink icon in the toolbar.</span></span>
    
14. <span data-ttu-id="c06b0-131">En **dirección URL**, escriba **http://www.spamlink.contoso.com/**, haga clic en **Aceptar**y, a continuación, haga clic en **Enviar**.</span><span class="sxs-lookup"><span data-stu-id="c06b0-131">In **URL**, type **http://www.spamlink.contoso.com/**, click **OK**, and then click **Send**.</span></span>
    
15. <span data-ttu-id="c06b0-132">Abra una instancia independiente de Internet Explorer en el modo de exploración privada, vaya al portal de Office 365 ([https://portal.office.com](https://portal.office.com)) e inicie sesión en su suscripción de prueba de Office 365 con su cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="c06b0-132">Open a separate instance of Internet Explorer in private browsing mode, go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)), and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
16. <span data-ttu-id="c06b0-133">Desde la página principal del portal, haga clic en el mosaico de aplicaciones y después en **Correo**.</span><span class="sxs-lookup"><span data-stu-id="c06b0-133">From the main portal page, click the apps tile, and then click **Mail**.</span></span>
    
17. <span data-ttu-id="c06b0-134">En la Bandeja de entrada, haga clic en el mensaje con el asunto **Sus nuevas claves**.</span><span class="sxs-lookup"><span data-stu-id="c06b0-134">In the Inbox, click the message with the subject **Your new keys**.</span></span>
    
18. <span data-ttu-id="c06b0-p103">En la carpeta correo electrónico no deseado, haga clic en el mensaje con el asunto del **nuevo sitio web de viajes**. En el mensaje, haga clic en el vínculo de **este sitio** . ¡Debería ver un "Oops! Página de Internet Explorer no pudo encontrar spamlink.contoso.com.". Esto es el resultado correcto, porque no hay ninguna página web en esa ubicación.</span><span class="sxs-lookup"><span data-stu-id="c06b0-p103">In the Junk Mail folder, click the message with the subject **New travel web site**. Within the message, click the **this site** link. You should see a "Oops! Internet Explorer could not find spamlink.contoso.com." page. This is the correct result because there is no web page at that location.</span></span>
    
<span data-ttu-id="c06b0-p104">Observe que ambos correos electrónicos potencialmente malintencionados se entregaron correctamente. El correo electrónico **Sus nuevas claves** podría contener software malintencionado no detectado y se permite al usuario hacer clic en el vínculo potencialmente malintencionado en el correo electrónico **Nuevo sitio web de viajes**.</span><span class="sxs-lookup"><span data-stu-id="c06b0-p104">Notice that both of these potentially malicious emails were delivered successfully. The **Your new keys** email could contain undetected malware and the user was allowed to click the potentially malicious link in the **New travel web site** email.</span></span>
  
## <a name="phase-3-configure-safe-attachment-and-safe-links-policies-for-atp"></a><span data-ttu-id="c06b0-143">Fase 3: Configurar directivas de vínculos y archivos adjuntos seguros de ATP</span><span class="sxs-lookup"><span data-stu-id="c06b0-143">Phase 3: Configure safe attachment and safe links policies for ATP</span></span>

<span data-ttu-id="c06b0-144">En esta fase, creará y configurará una directiva de datos adjuntos seguros para evitar que el correo electrónico con datos adjuntos potencialmente malintencionados se entregue y una directiva de vínculos seguros para evitar que los usuarios visiten direcciones URL potencialmente inseguras.</span><span class="sxs-lookup"><span data-stu-id="c06b0-144">In this phase, you create and configure a safe attachment policy to prevent email with potentially malicious attachments from being delivered and a safe links policy to keep users from traveling to potentially unsafe URLs.</span></span>
  
1. <span data-ttu-id="c06b0-145">En la ficha **Página principal de Microsoft Office** de Internet Explorer, haga clic en el icono de **administración** .</span><span class="sxs-lookup"><span data-stu-id="c06b0-145">On the **Microsoft Office Home** tab of Internet Explorer, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="c06b0-146">En el panel de navegación izquierdo, haga clic en **Centros de administración** y después en **Exchange**.</span><span class="sxs-lookup"><span data-stu-id="c06b0-146">In the left navigation, click **Admin centers**, and then **Exchange**.</span></span>
    
3. <span data-ttu-id="c06b0-147">En el panel de navegación izquierdo de la pestaña Centro de administración de Exchange, haga clic en **amenazas avanzadas**.</span><span class="sxs-lookup"><span data-stu-id="c06b0-147">In the left navigation of the Exchange admin center tab, click **advanced threats**.</span></span>
    
4. <span data-ttu-id="c06b0-148">Haga clic en la pestaña **datos adjuntos seguros** y después en el signo más.</span><span class="sxs-lookup"><span data-stu-id="c06b0-148">Click the **safe attachments** tab, and then click the plus sign.</span></span>
    
5. <span data-ttu-id="c06b0-149">En la ventana de la **nueva directiva de los datos adjuntos seguros** , en **nombre**, escriba **Directiva de datos adjuntos seguros - bloque**.</span><span class="sxs-lookup"><span data-stu-id="c06b0-149">In the **new safe attachments policy** window, in **Name**, type **Safe Attachment Policy - Block**.</span></span>
    
6. <span data-ttu-id="c06b0-150">**Respuesta de los datos adjuntos seguros malware desconocido**, haga clic en **Bloquear**.</span><span class="sxs-lookup"><span data-stu-id="c06b0-150">For **Safe attachments unknown malware response**, click **Block**.</span></span>
    
7. <span data-ttu-id="c06b0-151">En **Redirigir datos adjuntos al detectarlos**, haga clic en **Habilitar redirección** y escriba la dirección de correo electrónico de la cuenta de administrador global de Office 365.</span><span class="sxs-lookup"><span data-stu-id="c06b0-151">For **Redirect attachment on detection**, click **Enable redirect** and type the email address of your Office 365 global administrator account.</span></span>
    
8. <span data-ttu-id="c06b0-p105">Para **se aplica a**, haga clic en la flecha hacia abajo y, a continuación, haga clic en **el dominio de destinatario es**. En la ventana, haga clic en el nombre de su organización (por ejemplo, contoso.onmicrosoft.com) y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="c06b0-p105">For **Applied to**, click the down arrow, and then click **The recipient domain is**. In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
9. <span data-ttu-id="c06b0-p106">Haga clic en **Guardar**. Después de la actualización, debería ver la nueva y había habilitado la **Directiva de datos adjuntos seguros - bloque**.</span><span class="sxs-lookup"><span data-stu-id="c06b0-p106">Click **Save**. After the update, you should see the new and enabled **Safe Attachment Policy - Block**.</span></span>
    
10. <span data-ttu-id="c06b0-156">Haga clic en la pestaña **Vínculos seguros** y después en el signo más.</span><span class="sxs-lookup"><span data-stu-id="c06b0-156">Click the **safe links** tab, and then click the plus sign.</span></span>
    
11. <span data-ttu-id="c06b0-157">En la ventana **Nueva directiva de vínculos seguros**, escriba **Directiva de vínculos seguros** en **Nombre**.</span><span class="sxs-lookup"><span data-stu-id="c06b0-157">In the **new safe links policy** window, in **Name**, type **Safe Link Policy**.</span></span>
    
12. <span data-ttu-id="c06b0-158">En **Seleccionar la acción para direcciones URL potencialmente malintencionadas desconocidas en mensajes**, haga clic en **Activado** y seleccione **No permitir a los usuarios hacer clic en la dirección URL original**.</span><span class="sxs-lookup"><span data-stu-id="c06b0-158">For **Select the action for unknown potentially malicious URLs in messages**, click **On**, and then select **Do not allow users to click through to original URL**.</span></span>
    
13. <span data-ttu-id="c06b0-p107">Para **se aplica a**, haga clic en la flecha hacia abajo y, a continuación, haga clic en **el dominio de destinatario es**. En la ventana, haga clic en el nombre de su organización (por ejemplo, contoso.onmicrosoft.com) y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="c06b0-p107">For **Applied to**, click the down arrow, and then click **The recipient domain is**. In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
14. <span data-ttu-id="c06b0-p108">Haga clic en **Guardar**. Debería ver la nueva y habilitada **Directiva de vínculos seguros**.</span><span class="sxs-lookup"><span data-stu-id="c06b0-p108">Click **Save**. You should see the new and enabled **Safe Link Policy**.</span></span>
    
## <a name="phase-4-show-atp-in-action"></a><span data-ttu-id="c06b0-163">Fase 4: Mostrar ATP en acción</span><span class="sxs-lookup"><span data-stu-id="c06b0-163">Phase 4: Show ATP in action</span></span>

<span data-ttu-id="c06b0-164">En esta fase, veremos cómo ATP se gestiona el correo electrónico malintencionado.</span><span class="sxs-lookup"><span data-stu-id="c06b0-164">In this phase, you demonstrate how ATP deals with potentially malicious email.</span></span>
  
1. <span data-ttu-id="c06b0-165">En la instancia de Internet Explorer que usa para enviar el correo electrónico en la fase 2, en el panel de navegación izquierdo, haga clic en **elementos enviados.**</span><span class="sxs-lookup"><span data-stu-id="c06b0-165">From the instance of Internet Explorer that you used to send the email in Phase 2, in the left navigation, click **Sent Items.**</span></span>
    
2. <span data-ttu-id="c06b0-166">Haga clic en el correo electrónico titulado **las claves de nuevo**, haga clic en el icono de flecha hacia abajo y, a continuación, haga clic en **hacia delante**.</span><span class="sxs-lookup"><span data-stu-id="c06b0-166">Click the email titled **Your new keys**, click the down arrow icon, and then click **Forward**.</span></span>
    
3. <span data-ttu-id="c06b0-167">En el nuevo mensaje, en **Para**, escriba la dirección de correo electrónico del nombre de administrador global de Office 365 de su suscripción de prueba y después haga clic en **Enviar**.</span><span class="sxs-lookup"><span data-stu-id="c06b0-167">For the new message, in **To**, type the email address of the Office 365 global administrator name of your trial subscription, and then click **Send**.</span></span>
    
4. <span data-ttu-id="c06b0-168">Haga clic en el título **nuevo sitio web de viajes**de correo electrónico, haga clic en el icono de flecha hacia abajo, haga clic en **responder a todos**y, a continuación, haga clic en **Enviar**.</span><span class="sxs-lookup"><span data-stu-id="c06b0-168">Click the email titled **New travel web site**, click the down arrow icon, click **Reply all**, and then click **Send**.</span></span>
    
5. <span data-ttu-id="c06b0-p109">Desde la instancia de Internet Explorer que usó para configurar directivas de ATP en la fase 3, haga clic en la pestaña Centro de administración de Exchange, en el mosaico de aplicaciones y en **Correo**. Verá dos nuevos mensajes de correo electrónico en la Bandeja de entrada:</span><span class="sxs-lookup"><span data-stu-id="c06b0-p109">From the instance of Internet Explorer that you used to configure ATP policies in Phase 3, click the Exchange admin center tab, click the apps tile, and then click **Mail**. You should see two new email messages in the Inbox:</span></span>
    
  - <span data-ttu-id="c06b0-171">Uno titulado **RV: Sus nuevas claves**</span><span class="sxs-lookup"><span data-stu-id="c06b0-171">One titled **Fw: Your new keys**</span></span>
    
  - <span data-ttu-id="c06b0-172">Uno titulado **RV: Nuevo sitio web de viajes**</span><span class="sxs-lookup"><span data-stu-id="c06b0-172">One titled **Fw: New travel web site**</span></span>
    
6. <span data-ttu-id="c06b0-p110">Abra el mensaje de correo electrónico titulado **RV: nuevo sitio web de viajes** y haga clic en el vínculo de **este sitio** . Debería ver una página "este sitio Web ha sido clasificado como malintencionados.". Esto demuestra que ATP le impide tener acceso al sitio web potencialmente malintencionado.</span><span class="sxs-lookup"><span data-stu-id="c06b0-p110">Open the email message titled **Fw: New travel web site** and click the **this site** link. You should see a "This website has been classified as malicious." page. This demonstrates that ATP is preventing you from accessing the potentially malicious web site.</span></span>
    
7. <span data-ttu-id="c06b0-177">En la pestaña Centro de administración de Exchange de Internet Explorer, en el panel de exploración izquierdo, haga clic en **Flujo de correo**.</span><span class="sxs-lookup"><span data-stu-id="c06b0-177">In the Exchange admin center tab of Internet Explorer, in the left navigation, click **mail flow**.</span></span>
    
8. <span data-ttu-id="c06b0-178">Haga clic en la pestaña **Seguimiento de mensajes** y después en **Buscar**.</span><span class="sxs-lookup"><span data-stu-id="c06b0-178">Click the **message trace** tab, and then click **search**.</span></span>
    
9. <span data-ttu-id="c06b0-p111">En la ventana de **Resultados de seguimiento de mensajes** , haga doble clic en el mensaje con el asunto de **las claves de nuevo**. Este mensaje se entregó correctamente a la Bandeja de entrada. Cierre esta ventana.</span><span class="sxs-lookup"><span data-stu-id="c06b0-p111">In the **Message Trace Results** window, double-click the message with the subject **Your new keys**. This message was successfully delivered to the Inbox. Close this window.</span></span>
    
10. <span data-ttu-id="c06b0-p112">Haga doble clic en el mensaje con el asunto del **nuevo sitio web de viajes**. Este mensaje se entregó correctamente a la Bandeja de entrada. Cierre esta ventana.</span><span class="sxs-lookup"><span data-stu-id="c06b0-p112">Double-click the message with the subject **New travel web site**. This message was successfully delivered to the Inbox. Close this window.</span></span>
    
11. <span data-ttu-id="c06b0-p113">Haga doble clic en el mensaje con el asunto **RV: sus nuevas claves**. Tenga en cuenta cómo este mensaje se procesa ATP y, a continuación, se entrega a la Bandeja de entrada. Cierre esta ventana.</span><span class="sxs-lookup"><span data-stu-id="c06b0-p113">Double-click the message with the subject **Fw: Your new keys**. Note how this message was processed by ATP and then delivered to the Inbox. Close this window.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="c06b0-p114">El propósito de la directiva de los datos adjuntos seguros era empezar a explorar los datos adjuntos para código malintencionado. Los datos adjuntos de getKeys.js se permiten debido a que no se determinó malintencionada. En este paso se muestra que ATP realizar un examen de los datos adjuntos.</span><span class="sxs-lookup"><span data-stu-id="c06b0-p114">The purpose of the safe attachments policy was to begin scanning attachments for malicious code. The getKeys.js attachment was allowed because it was not determined to be malicious. This step shows that ATP did perform a scan of the attachment.</span></span> 
  
12. <span data-ttu-id="c06b0-p115">Haga doble clic en el mensaje con el asunto **RV: nuevo sitio web de viajes**. Tenga en cuenta que este mensaje se entregó correctamente a la Bandeja de entrada.</span><span class="sxs-lookup"><span data-stu-id="c06b0-p115">Double-click the message with the subject **Fw: New travel web site**. Note that this message was successfully delivered to the Inbox.</span></span>
    
<span data-ttu-id="c06b0-193">Ahora puede usar este entorno para crear nuevas directivas y experimentar con ATP.</span><span class="sxs-lookup"><span data-stu-id="c06b0-193">You can now use this environment to create new policies and experiment with ATP.</span></span>
  
> [!TIP]
> <span data-ttu-id="c06b0-194">Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual de todos los artículos en la pila de la Guía del entorno de pruebas de One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="c06b0-194">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c06b0-195">Vea también</span><span class="sxs-lookup"><span data-stu-id="c06b0-195">See Also</span></span>

[<span data-ttu-id="c06b0-196">Guías del laboratorio de pruebas de adopción de la nube (TLG)</span><span class="sxs-lookup"><span data-stu-id="c06b0-196">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="c06b0-197">Entorno de desarrollo y pruebas de la configuración básica</span><span class="sxs-lookup"><span data-stu-id="c06b0-197">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="c06b0-198">Entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="c06b0-198">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="c06b0-199">Sincronización de directorios (DirSync) para el entorno de desarrollo y prueba de Office 365</span><span class="sxs-lookup"><span data-stu-id="c06b0-199">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="c06b0-200">Seguridad de Cloud App para su entorno de desarrollo y prueba de Office 365</span><span class="sxs-lookup"><span data-stu-id="c06b0-200">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="c06b0-201">Adopción de la nube y soluciones híbridas</span><span class="sxs-lookup"><span data-stu-id="c06b0-201">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md) 

[<span data-ttu-id="c06b0-202">Protección contra amenazas avanzada para datos adjuntos seguros y vínculos seguros</span><span class="sxs-lookup"><span data-stu-id="c06b0-202">Advanced threat protection for safe attachments and safe links</span></span>](https://support.office.com/article/Office-365-Advanced-Threat-Protection-E100FE7C-F2A1-4B7D-9E08-622330B83653)


