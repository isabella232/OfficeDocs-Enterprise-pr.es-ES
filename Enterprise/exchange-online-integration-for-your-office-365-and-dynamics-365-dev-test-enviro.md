---
title: Integración de Exchange Online para su entorno de desarrollo y pruebas y de Office 365 y 365 de Dynamics
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
ms.custom: Ent_TLGs
ms.assetid: 499c5823-427a-4ba2-8fc1-9553bc2ff2d3
description: 'Resumen: Utilice a esta guía del entorno de pruebas para habilitar la integración de Dynamics 365 para Exchange Online en su suscripción de prueba de Office 365.'
ms.openlocfilehash: 47153f9321284d0bb30f59645dfe56ab40cb7982
ms.sourcegitcommit: 201d3338d8bbc6da9389e62e2add8a17384fab4d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "31038004"
---
# <a name="exchange-online-integration-for-your-office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="daf69-103">Integración de Exchange Online para su entorno de desarrollo y pruebas y de Office 365 y 365 de Dynamics</span><span class="sxs-lookup"><span data-stu-id="daf69-103">Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment</span></span>

 <span data-ttu-id="daf69-104">**Resumen:** Utilice a esta guía del entorno de pruebas para habilitar la integración de Dynamics 365 para Exchange Online en su suscripción de prueba de Office 365.</span><span class="sxs-lookup"><span data-stu-id="daf69-104">**Summary:** Use this Test Lab Guide to enable Dynamics 365 integration for Exchange Online in your Office 365 trial subscription.</span></span>
  
<span data-ttu-id="daf69-p101">Una de las características más útiles de Microsoft Dynamics 365 es la de almacenar todas las comunicaciones con los clientes en un solo lugar, de modo que cualquier usuario con los permisos adecuados puede ver todos los registros pertinentes de clientes. Por ejemplo, ver todo el correo electrónico asociado a un contacto, a una cuenta, a una oportunidad o a un caso determinados.</span><span class="sxs-lookup"><span data-stu-id="daf69-p101">A valuable use of Microsoft Dynamics 365 is to store all customer communications in one place, so anyone with the appropriate permissions can see all relevant customer records. For example, view all email associated with a particular contact, account, opportunity, or case.</span></span>
  
<span data-ttu-id="daf69-p102">Para almacenar el correo electrónico y otros registros de mensajes en Dynamics 365, debe sincronizar su sistema de correo electrónico con Dynamics 365. La sincronización del lado del servidor es el método preferido para la sincronización de correo electrónico.</span><span class="sxs-lookup"><span data-stu-id="daf69-p102">To store email and other messaging records in Dynamics 365, you need to synchronize your email system with Dynamics 365. Server-side synchronization is the method of choice for email synchronization.</span></span>
  
<span data-ttu-id="daf69-109">Utilice a esta guía del entorno de pruebas para configurar y mostrar cómo Exchange Online y el cliente de Outlook Online pueden aprovechar la información almacenada en Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="daf69-109">Use this Test Lab Guide to configure and demonstrate how Exchange Online and the Outlook Online client can leverage the information stored in Dynamics 365.</span></span> 
  
## <a name="phase-1-build-out-the-office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="daf69-110">Fase 1: Crear el entorno de desarrollo y pruebas de Office 365 y Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="daf69-110">Phase 1: Build out the Office 365 and Dynamics 365 dev/test environment</span></span>

<span data-ttu-id="daf69-111">Siga las instrucciones de [Entorno de desarrollo y pruebas de Office 365 y Dynamics 365](office-365-and-dynamics-365-dev-test-environment.md) para crear una versión ligera o de empresa simulada de un entorno de desarrollo y pruebas de Office 365 y Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="daf69-111">Use the instructions in [Office 365 and Dynamics 365 dev/test environment](office-365-and-dynamics-365-dev-test-environment.md) to create either a lightweight or simulated enterprise version of an Office 365 and Dynamics 365 dev/test environment.</span></span>
  
> [!NOTE]
> <span data-ttu-id="daf69-112">La configuración de este artículo no requiere el entorno de desarrollo y pruebas de una empresa simulada, que incluye una intranet simulada conectada a Internet y la sincronización de directorios para un bosque de servicios de dominio de Active Directory (AD DS).</span><span class="sxs-lookup"><span data-stu-id="daf69-112">The configuration in this article does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for an Active Directory Domain Services (AD DS) forest.</span></span> <span data-ttu-id="daf69-113">Aquí se ofrece como opción para que pueda experimentar con Office 365 y Dynamics 365 en un entorno que representa una organización típica.</span><span class="sxs-lookup"><span data-stu-id="daf69-113">It is provided here as an option so that you can experiment with Office 365 and Dynamics 365 in an environment that represents a typical organization</span></span> 
  
## <a name="phase-2-configure-and-demonstrate-dynamics-365-integration-in-exchange-online"></a><span data-ttu-id="daf69-114">Fase 2: Configurar y mostrar la integración de Dynamics 365 en Exchange Online</span><span class="sxs-lookup"><span data-stu-id="daf69-114">Phase 2: Configure and demonstrate Dynamics 365 integration in Exchange Online</span></span>

<span data-ttu-id="daf69-115">Siga estos pasos para configurar el buzón del administrador global para la integración de Dynamics 365 y Exchange Online:</span><span class="sxs-lookup"><span data-stu-id="daf69-115">Use these steps to configure the global administrator's mailbox for Dynamics 365 and Exchange Online integration:</span></span>
  
1. <span data-ttu-id="daf69-116">Con una sesión privada del explorador, vaya a [http://admin.microsoft.com](http://admin.microsoft.com) e inicie sesión con su cuenta de administrador global de Office 365.</span><span class="sxs-lookup"><span data-stu-id="daf69-116">Using a private session of your browser, go to [http://admin.microsoft.com](http://admin.microsoft.com) and sign in using your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="daf69-117">En la **Página principal de Microsoft Office**, haga clic en el icono de **Correo**.</span><span class="sxs-lookup"><span data-stu-id="daf69-117">On the **Microsoft Office Home** page, click the **Mail** tile.</span></span>
    
3. <span data-ttu-id="daf69-118">En la nueva pestaña **correo** del explorador, haga clic en **nuevo** y observe que la esquina inferior del panel debajo del cuadro para escribir un mensaje tiene un icono para mis plantillas.</span><span class="sxs-lookup"><span data-stu-id="daf69-118">On the new **Mail** tab in your browser, click **New** and notice how the bottom corner of the pane below the box for typing a message has an icon for My Templates.</span></span>
    
     ![Un mensaje de correo electrónico nuevo en blanco sin integración con Dynamics 365.](media/879b54fd-a68f-4581-9f89-d5050df6f4de.png)
  
4. <span data-ttu-id="daf69-120">Haga clic en **Descartar** y deje abierta la pestaña **Correo**.</span><span class="sxs-lookup"><span data-stu-id="daf69-120">Click **Discard** and leave the **Mail** tab open.</span></span>
    
5. <span data-ttu-id="daf69-121">Haga clic en la pestaña **Página principal de Microsoft Office** del explorador y, a continuación, en el icono **Admin**.</span><span class="sxs-lookup"><span data-stu-id="daf69-121">Click the **Microsoft Office Home** tab in your browser, and then click the **Admin** tile.</span></span>
    
6. <span data-ttu-id="daf69-122">En el panel de navegación izquierdo de la pestaña **Centro de administración de Office**, haga clic en **Centros de administración > Dynamics 365**.</span><span class="sxs-lookup"><span data-stu-id="daf69-122">In the left navigation of the **Office Admin center** tab, click **Admin centers > Dynamics 365**.</span></span>
    
7. <span data-ttu-id="daf69-123">En la nueva pestaña **Dynamics 365** del explorador, en la lista de instancias de Dynamics 365, haga clic en **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="daf69-123">On the new **Dynamics 365** tab in your browser, in the list of Dynamics 365 instances, click **Open**.</span></span>
    
8. <span data-ttu-id="daf69-124">En la nueva pestaña **Administración** del explorador, en la barra de navegación, haga clic en la flecha hacia abajo junto a **Configuración** y, a continuación, en **Configuración de correo electrónico**, en **Sistema**.</span><span class="sxs-lookup"><span data-stu-id="daf69-124">On the new **Administration** tab in your browser, on the navigation bar, click the down arrow next to **Settings**, and then click **Email Configuration** under **System**.</span></span>
    
9.  <span data-ttu-id="daf69-125">En la página **Configuración de correo electrónico**, haga clic en **Opciones de configuración de correo electrónico**.</span><span class="sxs-lookup"><span data-stu-id="daf69-125">On the **Email Configuration** page, click **Email Configuration Settings**.</span></span>
    
10. <span data-ttu-id="daf69-126">En la pestaña **Correo electrónico** del cuadro de diálogo **Configuración del sistema**, cambie **Citas, contactos y tareas** a **Sincronización del lado del servidor** y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="daf69-126">In the **Email** tab on the **System Settings** dialog box, change **Appointments, Contacts, and Tasks** to **Server-Side Synchronization**, and then click **OK**.</span></span>
    
11. <span data-ttu-id="daf69-127">En la página **Configuración de correo electrónico**, haga clic en **Buzones**.</span><span class="sxs-lookup"><span data-stu-id="daf69-127">On the **Email Configuration** page, click **Mailboxes**.</span></span>
    
12. <span data-ttu-id="daf69-128">Seleccione el nombre de administrador global de Office 365 en la columna izquierda de marca de verificación, haga clic en **Aplicar configuración de correo electrónico predeterminada** en la barra de herramientas y, a continuación, en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="daf69-128">Select the Office 365 global administrator name in the left check mark column, click **Apply Default Email Settings** in the tool bar, and then click **OK**.</span></span>
    
13. <span data-ttu-id="daf69-129">En la barra de herramientas, haga clic en **Aprobar correo electrónico** y, a continuación, en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="daf69-129">Click **Approve Email** in the tool bar, and then click **OK**.</span></span>
    
14. <span data-ttu-id="daf69-130">Seleccione el nombre de administrador global de Office 365 en la columna izquierda de marca de verificación, haga clic en **Probar y habilitar buzones** en la barra de herramientas y, después, en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="daf69-130">Select the Office 365 global administrator name in the left check mark column, click **Test &amp; Enable Mailboxes** in the tool bar, and then click **OK**.</span></span>
    
15. <span data-ttu-id="daf69-131">Haga clic en la pestaña abierta **Correo** y compruebe que el administrador global haya recibido un mensaje de prueba.</span><span class="sxs-lookup"><span data-stu-id="daf69-131">Click the open **Mail** tab and confirm that the global administrator received a test message.</span></span>
    
16. <span data-ttu-id="daf69-p104">Vuelva a la pestaña **Mis buzones activos** del navegador y actualice la página. Las columnas **Estado del correo electrónico entrante** y **Estado del correo electrónico saliente** deben establecerse en **Correcto** para el nombre de la cuenta de administrador global. Tenga en cuenta que pueden ser necesarios hasta 15 minutos para completar ambas pruebas.</span><span class="sxs-lookup"><span data-stu-id="daf69-p104">Return to the **Mailboxes My Active Mailboxes** tab in your browser and refresh the page. The **Incoming Email Status** and **Outgoing Email Status** columns should be set to **Success** for the global administrator account name. Note that it can take up to 15 minutes to complete both tests.</span></span>
    
<span data-ttu-id="daf69-135">Siga estos pasos para instalar la aplicación Dynamics 365 para Outlook y mostrar las características de Dynamics 365 dentro del buzón de administrador global:</span><span class="sxs-lookup"><span data-stu-id="daf69-135">Use these steps to install the Dynamics 365 App for Outlook and demonstrate Dynamics 365 features within the global administrator's mailbox:</span></span>
  
1. <span data-ttu-id="daf69-136">En la pestaña **Mis buzones activos** del explorador, haga clic en la flecha hacia abajo junto a **Configuración** y, a continuación, en **aplicación Dynamics 365 para Outlook**, en **Sistema**.</span><span class="sxs-lookup"><span data-stu-id="daf69-136">On the **Mailboxes My Active Mailboxes** tab in your browser, click the down arrow next to **Settings**, and then click **Dynamics 365 App for Outlook** under **System**.</span></span>
    
2. <span data-ttu-id="daf69-p105">En la página **Introducción a la aplicación de Microsoft Dynamics 365 para Outlook**, haga clic en el nombre de administrador global y, a continuación, en **Agregar aplicación a Outlook**. La columna **Estado** cambiará a **Pendiente**.</span><span class="sxs-lookup"><span data-stu-id="daf69-p105">On the **Getting Started with Microsoft Dynamics 365 App for Outlook** page, click the global administrator name, and then click **Add App to Outlook**. The **Status** column changes to **Pending**.</span></span>
    
3. <span data-ttu-id="daf69-p106">Actualice la página hasta que cambie el estado a **Agregado a Outlook**. Tenga en cuenta que pueden ser necesarios hasta 15 minutos para completar la configuración.</span><span class="sxs-lookup"><span data-stu-id="daf69-p106">Refresh the page until the status changes to **Added to Outlook**. Note that it can take up to 15 minutes to complete this configuration.</span></span>
    
4. <span data-ttu-id="daf69-141">Haga clic en la pestaña **Correo** en el explorador y, a continuación, ciérrela.</span><span class="sxs-lookup"><span data-stu-id="daf69-141">Click on the **Mail** tab in your browser and then close it.</span></span>
    
5. <span data-ttu-id="daf69-142">Haga clic en la pestaña **Página principal de Microsoft Office** del explorador y, a continuación, en el icono **Correo**.</span><span class="sxs-lookup"><span data-stu-id="daf69-142">Click the **Microsoft Office Home** tab in your browser, and then click the **Mail** tile.</span></span>
    
6. <span data-ttu-id="daf69-143">En la nueva pestaña **Correo** del explorador, haga clic en **Nuevo**.</span><span class="sxs-lookup"><span data-stu-id="daf69-143">On the new **Mail** tab in your browser, click **New**.</span></span> <span data-ttu-id="daf69-144">Observe que la esquina inferior del panel debajo del cuadro para escribir un mensaje ahora tiene un icono para Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="daf69-144">Notice that the bottom corner of the pane below the box for typing a message now has an icon for Dynamics 365.</span></span>
    
     ![Un mensaje de correo electrónico nuevo en blanco con integración con Dynamics 365, en el que se muestra el icono nuevo.](media/ecb822e1-45fe-4481-99a1-294317d1d2de.png)
  
7. <span data-ttu-id="daf69-p108">Haga clic en el icono de Dynamics 365. Verá un panel de **Dynamics 365**, desde el que puede realizar el seguimiento de este correo electrónico o acceder a plantillas, documentación de ventas o artículos.</span><span class="sxs-lookup"><span data-stu-id="daf69-p108">Click the Dynamics 365 icon. You should see a **Dynamics 365** pane, from which you can track this email or access templates, sales literature, or articles.</span></span>
    
8. <span data-ttu-id="daf69-p109">En el campo **Para** del mensaje de correo electrónico, escriba **alex.y.wu@outlook.com** y, a continuación, haga clic en **Reintentar** en el panel de **Dynamics 365**. Verá la sección **Destinatarios** en el panel de **Dynamics 365** con información sobre Alex Wu, un contacto de la aplicación de ventas que se proporcionó con los datos de ejemplo de su suscripción de prueba.</span><span class="sxs-lookup"><span data-stu-id="daf69-p109">In the **To** field of the email message, type **alex.y.wu@outlook.com**, and then click **Retry** in the **Dynamics 365** pane. You should see a **Recipients** section in the **Dynamics 365** pane with information on Alex Wu, a contact from the sales application that was provided with the sample data for your trial subscription.</span></span>
    
     ![El panel de información de Dynamics 365 de un contacto de ventas almacenado en Dynamics 365.](media/a010fa5f-3f1b-47d4-ab5e-d00d85a24a3f.png)
  
9. <span data-ttu-id="daf69-151">Haga clic en **Descartar**.</span><span class="sxs-lookup"><span data-stu-id="daf69-151">Click **Discard**.</span></span>

> [!TIP]
> <span data-ttu-id="daf69-152">Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual de todos los artículos en la pila de la Guía del entorno de pruebas de One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="daf69-152">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="daf69-153">Consulte también</span><span class="sxs-lookup"><span data-stu-id="daf69-153">See Also</span></span>

[<span data-ttu-id="daf69-154">Entorno de desarrollo y pruebas de Office 365 y Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="daf69-154">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
  
[<span data-ttu-id="daf69-155">Guías del laboratorio de pruebas de adopción de la nube (TLG)</span><span class="sxs-lookup"><span data-stu-id="daf69-155">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="daf69-156">Entorno de desarrollo y pruebas de la configuración básica</span><span class="sxs-lookup"><span data-stu-id="daf69-156">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="daf69-157">Entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="daf69-157">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="daf69-158">Sincronización de directorios (DirSync) para el entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="daf69-158">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)

[<span data-ttu-id="daf69-159">Administración de suscripción para Dynamics 365 (online)</span><span class="sxs-lookup"><span data-stu-id="daf69-159">Subscription Management for Dynamics 365 (online)</span></span>](https://technet.microsoft.com/library/jj679903.aspx)
  
[<span data-ttu-id="daf69-160">Administración de Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="daf69-160">Administering Dynamics 365</span></span>](https://technet.microsoft.com/library/dn531101.aspx)


