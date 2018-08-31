---
title: 'Recuperar elementos eliminados en un buzón de usuario: ayuda para administradores'
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: eb15194b-63ec-41b0-8d90-1823d3f558e4
description: 'En este artículo está dirigido a administradores. ¿Un usuario eliminar permanentemente los elementos de su buzón de Outlook? El usuario copia lo solicite, pero no puede recuperarlos. Es posible que pueda recuperar los elementos purgados si aún no se han quitado permanentemente el buzón del usuario. '
ms.openlocfilehash: abfc0a1a35d8e694197e12d05a2206dd4e3eb37a
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542764"
---
# <a name="recover-deleted-items-in-a-user-mailbox---admin-help"></a><span data-ttu-id="c4b8c-106">Recuperar elementos eliminados en un buzón de usuario: ayuda para administradores</span><span class="sxs-lookup"><span data-stu-id="c4b8c-106">Recover deleted items in a user mailbox - Admin Help</span></span>

<span data-ttu-id="c4b8c-p102">**Este artículo está dirigido a administradores. Está intentando recuperar elementos eliminados en su propio buzón de correo?** Pruebe con uno de los procedimientos siguientes:</span><span class="sxs-lookup"><span data-stu-id="c4b8c-p102">**This article is for administrators. Are you trying to recover deleted items in your own mailbox?** Try one of the following:</span></span>
- [<span data-ttu-id="c4b8c-109">Recuperación de elementos eliminados en Outlook para Windows</span><span class="sxs-lookup"><span data-stu-id="c4b8c-109">Recover deleted items in Outlook for Windows</span></span>](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
- [<span data-ttu-id="c4b8c-110">Recuperar elementos eliminados o correo electrónico en Outlook Web App</span><span class="sxs-lookup"><span data-stu-id="c4b8c-110">Recover deleted items or email in Outlook Web App</span></span>](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
- [<span data-ttu-id="c4b8c-111">Restauración de los mensajes de correo electrónico eliminados en Outlook en el web</span><span class="sxs-lookup"><span data-stu-id="c4b8c-111">Restore deleted email messages in Outlook on the web</span></span>](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
- [<span data-ttu-id="c4b8c-112">Outlook.com</span><span class="sxs-lookup"><span data-stu-id="c4b8c-112">Outlook.com</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=623435)
   
<span data-ttu-id="c4b8c-p103">¿Un usuario eliminar permanentemente los elementos de su buzón de Outlook? El usuario copia lo solicite, pero no puede recuperarlos. Es posible que pueda recuperar los elementos purgados si aún no se han quitado permanentemente el buzón del usuario. Hacerlo mediante la herramienta de exhibición de documentos electrónicos en contexto en Exchange Online para buscar correo electrónico eliminado y otros elementos y como contactos, citas de calendario y tareas, en el buzón del usuario. Si observa los elementos eliminados, puede exportarlos a un archivo PST (también denominado un archivo de datos de Outlook), que el usuario, a continuación, puede usar para restaurar los elementos en su buzón.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-p103">Did a user permanently delete items from their Outlook mailbox? The user wants them back but can't recover them. You may be able recover the purged items if they haven't been permanently removed from the user's mailbox. You do this by using the In-Place eDiscovery tool in Exchange Online to search for deleted email and other items—and such as contacts, calendar appointments, and tasks—in a user's mailbox. If you find the deleted items, you can export them to a PST file (also called an Outlook Data File), which the user can then use to restore the items back to their mailbox.</span></span>
  
<span data-ttu-id="c4b8c-p104">Estos son los pasos para recuperar los elementos eliminados en el buzón del usuario. ¿Cuánto tiempo tardará esto? La primera vez puede tardar 20 o 30 minutos para completar todos los pasos, según el número de elementos está intentando recuperar.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-p104">Here are the steps for recovering deleted items in a user's mailbox. How long will this take? The first time might take 20 or 30 minutes to complete all the steps, depending on how many items you're trying to recover.</span></span>
  
> [!NOTE]
> <span data-ttu-id="c4b8c-p105">Tiene que ser un **Administrador de Exchange** o un **Administrador Global** en Office 365 o ser miembro del grupo de roles de administración de la organización de Exchange en línea para llevar a cabo los pasos de este artículo. Para obtener más información, vea [roles de administrador acerca de Office 365](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span><span class="sxs-lookup"><span data-stu-id="c4b8c-p105">You have to be an **Exchange administrator** or **Global administrator** in Office 365 or be a member of the Organization Management role group in Exchange Online to perform the steps in this article. For more information, see [About Office 365 admin roles](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span></span> 
  
## <a name="step-1-assign-yourself-ediscovery-permissions"></a><span data-ttu-id="c4b8c-123">Paso 1: Asignar permisos de exhibición de documentos electrónicos</span><span class="sxs-lookup"><span data-stu-id="c4b8c-123">Step 1: Assign yourself eDiscovery permissions</span></span>
<span data-ttu-id="c4b8c-124"><a name="step1"> </a></span><span class="sxs-lookup"><span data-stu-id="c4b8c-124"></span></span>

<span data-ttu-id="c4b8c-p106">El primer paso consiste en asignar usted mismo los permisos necesarios en Exchange Online por lo que puede usar la herramienta de exhibición de documentos electrónicos en contexto para buscar el buzón de un usuario. Solo tiene que hacer esto una vez. Si tiene que buscar otro buzón en el futuro, puede omitir este paso.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-p106">The first step is to assign yourself the necessary permissions in Exchange Online so you can use the In-Place eDiscovery tool to search a user's mailbox. You only have to do this once. If you have to search another mailbox in the future, you can skip this step.</span></span>
  
1. <span data-ttu-id="c4b8c-128">[Where iniciar sesión en Office 365 para la empresa](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) con su cuenta de trabajo o escuela.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-128">[Where to sign in to Office 365 for business](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) with your work or school account.</span></span> 
    
2. <span data-ttu-id="c4b8c-129">Seleccione el icono del selector de aplicación ![el icono del selector de aplicación en Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) en la superior izquierda y haga clic en **Admin**.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-129">Select the app launcher icon ![The app launcher icon in Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) in the upper-left and click **Admin**.</span></span>
    
3. <span data-ttu-id="c4b8c-130">En la izquierda en el centro de administración de Office 365, expanda **centros de administración**y, a continuación, haga clic en **Exchange**.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-130">In the left navigation in the Office 365 admin center, expand **Admin centers**, and then click **Exchange**.</span></span>
    
    ![Lista del centro de administración](media/7d308eb7-ba63-4156-a845-3770facc5de4.PNG)
  
4. <span data-ttu-id="c4b8c-132">En el centro de administración de Exchange, haga clic en **permisos**y, a continuación, haga clic en **roles de administrador**.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-132">In the Exchange admin center, click **Permissions**, and then click **Admin roles**.</span></span>
    
5. <span data-ttu-id="c4b8c-133">En la vista de lista, seleccione **Administración de detección**y, a continuación, haga clic en **Editar**![icono Editar](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif).</span><span class="sxs-lookup"><span data-stu-id="c4b8c-133">In the list view, select **Discovery Management**, and then click **Edit**![Edit icon](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif).</span></span>
    
    ![Agregarse a sí mismo al grupo de funciones de administración de detección en el EAC](media/e5c98e93-d6a0-40c5-a143-bac956eedaa7.png)
  
6. <span data-ttu-id="c4b8c-135">En el **Grupo de roles**, en **miembros**, haga clic en **Agregar**![icono Agregar](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span><span class="sxs-lookup"><span data-stu-id="c4b8c-135">In **Role Group**, under **Members**, click **Add**![Add icon](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
7. <span data-ttu-id="c4b8c-136">En **Seleccionar miembros**, seleccione usted mismo de la lista de nombres, haga clic en **Agregar**y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-136">In **Select Members**, select yourself from the list of names, click **Add**, and then click **OK**.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="c4b8c-p107">También puede agregar un grupo que es un miembro de, como administración de la organización o TenantAdmins. Si agrega un grupo, se asignará a otros miembros del grupo de los permisos necesarios para ejecutar la herramienta de exhibición de documentos electrónicos en contexto.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-p107">You can also add a group that you are a member of, such as Organization Management or TenantAdmins. If you add a group, other members of the group will be assigned the necessary permissions to run the In-Place eDiscovery tool.</span></span> 
  
8. <span data-ttu-id="c4b8c-139">En **Grupo de roles**, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-139">In **Role Group**, click **Save**.</span></span>
    
9. <span data-ttu-id="c4b8c-140">Cerrar la sesión de Office 365.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-140">Sign out of Office 365.</span></span>
    
    <span data-ttu-id="c4b8c-141">Se debe cerrar la sesión antes de iniciar el paso siguiente para que los nuevos permisos surta efecto.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-141">You have to sign out before you start the next step so the new permissions will take effect.</span></span>
    
> [!CAUTION]
> <span data-ttu-id="c4b8c-p108">Los miembros del grupo de roles de administración de detección pueden tener acceso a contenido de mensaje confidencial. Esto incluye la búsqueda de todos los buzones en la organización, obtener una vista previa de los resultados de búsqueda (y otros elementos del buzón de correo), copiar los resultados a un buzón de detección y exportar los resultados de búsqueda a un archivo PST.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-p108">Members of the Discovery Management role group can access sensitive message content. This includes searching all mailboxes in your organization, previewing the search results (and other mailbox items), copying the results to a discovery mailbox, and exporting the search results to a PST file.</span></span> 
  
[<span data-ttu-id="c4b8c-144">Return to top</span><span class="sxs-lookup"><span data-stu-id="c4b8c-144">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-2-search-the-users-mailbox-for-deleted-items"></a><span data-ttu-id="c4b8c-145">Paso 2: Buscar el buzón del usuario para los elementos eliminados</span><span class="sxs-lookup"><span data-stu-id="c4b8c-145">Step 2: Search the user's mailbox for deleted items</span></span>
<span data-ttu-id="c4b8c-146"><a name="step2"> </a></span><span class="sxs-lookup"><span data-stu-id="c4b8c-146"></span></span>

<span data-ttu-id="c4b8c-p109">Cuando se ejecuta una búsqueda de exhibición de documentos electrónicos en contexto, la carpeta elementos recuperables en el buzón de correo que buscar, automáticamente se incluye en la búsqueda. La carpeta elementos recuperables es donde se almacenan los elementos eliminados de forma permanente hasta que está purgar (quita permanentemente) desde el buzón de correo. Por lo tanto, si todavía no se han purgado un elemento, debe ser capaz de encontrar mediante la herramienta de exhibición de documentos electrónicos en contexto.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-p109">When you run an In-Place eDiscovery search, the Recoverable Items folder in the mailbox that you search is automatically included in the search. The Recoverable Items folder is where permanently deleted items are stored until they're purged (permanently removed) from the mailbox. So, if an item hasn't been purged, you should be able to find it by using the In-Place eDiscovery tool.</span></span>
  
1. <span data-ttu-id="c4b8c-150">[Where iniciar sesión en Office 365 para la empresa](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) con su cuenta de trabajo o escuela.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-150">[Where to sign in to Office 365 for business](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) with your work or school account.</span></span> 
    
2. <span data-ttu-id="c4b8c-151">Seleccione el icono del selector de aplicación ![el icono del selector de aplicación en Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) en la superior izquierda y haga clic en **Admin**.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-151">Select the app launcher icon ![The app launcher icon in Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) in the upper-left and click **Admin**.</span></span>
    
3. <span data-ttu-id="c4b8c-152">En la izquierda en el centro de administración de Office 365, expanda **administración**y, a continuación, haga clic en **Exchange**.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-152">In the left navigation in the Office 365 admin center, expand **Admin**, and then click **Exchange**.</span></span>
    
4. <span data-ttu-id="c4b8c-153">En el centro de administración de Exchange, haga clic en **administración de cumplimiento**, haga clic en **en-exhibición de documentos electrónicos &amp; suspensión**y, a continuación, haga clic en **nuevo**![icono Agregar](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span><span class="sxs-lookup"><span data-stu-id="c4b8c-153">In the Exchange admin center, click **Compliance management**, click **In-Place eDiscovery &amp; Hold**, and then click **New**![Add icon](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
    ![En el CEF, en la página de administración de cumplimiento, haga clic en la exhibición de documentos electrónicos en contexto y retención](media/9d9ff0f5-b9be-45b8-8b5e-6037a856b0a8.png)
  
5. <span data-ttu-id="c4b8c-155">En la página **nombre y descripción** , escriba un nombre para la búsqueda (por ejemplo, el nombre del usuario que va a recuperar el correo electrónico para), una descripción opcional y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-155">On the **Name and description** page, type a name for the search (such as the name of the user you're recovering email for), an optional description, and then click **Next**.</span></span>
    
6. <span data-ttu-id="c4b8c-156">En la página de **los buzones de correo** , haga clic en **especificar los buzones de correo para buscar**y, a continuación, haga clic en **Agregar**![icono Agregar](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span><span class="sxs-lookup"><span data-stu-id="c4b8c-156">On the **Mailboxes** page, click **Specify mailboxes to search**, and then click **Add**![Add icon](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
    ![Haga clic en especificar los buzones de correo para buscar para buscar un buzón de correo específicas](media/83879a40-5e5c-49a8-be3b-c0023d197588.png)
  
7. <span data-ttu-id="c4b8c-158">Busque y seleccione el nombre del usuario que va a recuperar el correo electrónico eliminado para, haga clic en **Agregar**y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-158">Find and select the name of the user that you're recovering the deleted email for, click **Add**, and then click **OK**.</span></span>
    
8. <span data-ttu-id="c4b8c-159">Haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-159">Click **Next**.</span></span>
    
    <span data-ttu-id="c4b8c-p110">Se abrirá la página de **consulta de búsqueda** . Esto es donde se definen los criterios de búsqueda que le ayudará a encontrar los elementos que faltan en el buzón del usuario.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-p110">The **Search query** page is displayed. This is where you define the search criteria that will help you find the missing items in user's mailbox.</span></span> 
    
9. <span data-ttu-id="c4b8c-162">En la página **Consulta de búsqueda**, complete los campos siguientes:</span><span class="sxs-lookup"><span data-stu-id="c4b8c-162">On the **Search query** page, complete the following fields:</span></span> 
    
  - <span data-ttu-id="c4b8c-p111">**Incluir todo el contenido** Seleccione esta opción para incluir todo el contenido en el buzón del usuario en los resultados de búsqueda. Si selecciona esta opción, no puede especificar criterios de búsqueda adicionales.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-p111">**Include all content** Select this option to include all content in the user's mailbox in the search results. If you select this option, you can't specify additional search criteria.</span></span> 
    
  - <span data-ttu-id="c4b8c-165">**Filtro basado en criterios** Seleccione esta opción para especificar los criterios de búsqueda, incluidas las palabras clave, iniciar y finalizar las fechas, remitente y las direcciones de destinatario y tipos de mensajes.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-165">**Filter based on criteria** Select this option to specify the search criteria, including keywords, start and end dates, sender and recipient addresses, and message types.</span></span> 
    
    ![Crear una búsqueda basada en criterios como palabras clave, intervalo de fechas, los destinatarios y tipos de mensajes](media/ee47b833-9122-46a0-85e6-fcbe25be0dd5.png)
  
|<span data-ttu-id="c4b8c-167">**Campo**</span><span class="sxs-lookup"><span data-stu-id="c4b8c-167">**Field**</span></span>|<span data-ttu-id="c4b8c-168">**Utilice esta página para...**</span><span class="sxs-lookup"><span data-stu-id="c4b8c-168">**Use this to...**</span></span>|
|:-----|:-----|
|![Número uno en un círculo rosado](media/a4da261d-2516-48c5-b58a-9c452b9086b8.png)           <br/> |<span data-ttu-id="c4b8c-170">Especificar las palabras clave, intervalo de fechas, los destinatarios y tipos de mensajes.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-170">Specify keywords, date range, recipients, and message types.</span></span>  <br/> |
|![Número dos en un círculo rosado.](media/de3c1ab4-4f01-4026-b1ba-3265bdb32a89.png)           <br/> |<span data-ttu-id="c4b8c-172">Para los mensajes con las palabras clave o frases de búsqueda y usar operadores lógicos, como **AND** u **OR**.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-172">Search for messages with keywords or phrases, and use logical operators such as **AND** or **OR**.</span></span>  <br/> |
|![Número tres en un círculo rosado.](media/60fa378c-6ac1-4cbd-a782-2fa7ca619dc6.png)           <br/> |<span data-ttu-id="c4b8c-174">Buscar los mensajes enviados o recibidos dentro de un intervalo de fechas.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-174">Search for messages sent or received within a date range.</span></span>  <br/> |
|![Número 4 en un círculo rosado.](media/1a0ff2ce-0942-405a-94e3-9bfeb1e5059e.png)           <br/> |<span data-ttu-id="c4b8c-176">Buscar mensajes del recibidos o enviados a personas específicas.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-176">Search for messages received from or sent to specific people.</span></span>  <br/> |
|![Número cinco en un círculo rosado.](media/878cc815-0165-49ba-a1ee-9236e5980403.png)           <br/> |<span data-ttu-id="c4b8c-178">Buscar todos los tipos de mensajes o seleccione los que desee.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-178">Search for all message types or select specific ones.</span></span>  <br/> |
   
    > [!TIP]
    >  Here's a few tips about how to build a search query to find missing items. Try to get as much information from the user to help you create a search query so you can find what you're looking for. >  If you not sure how to find a missing message, consider using the **Include all content** option. The search results will include all items in the user's Recoverable Items folder, including the hidden folder (called the Purges folder) that contain items that have been purged by the user. Then you can go to Step 3, copy the results to a discovery mailbox, and look at the message in the hidden folder. >  If you know approximately when the missing message was originally sent or received by the user, use the **Specify start date** and **Specify end date** options to provide a date range. This will return all messages sent or received by the user within that date range. Specifying a date range is a really good way to narrow the search results. >  If you know who sent the missing email, use the **From** box to specify this sender. >  If you want to narrow the search results to different types of mailbox items, click **Select message types**, click **Select the message types to search**, and then choose a specific message type to search for. For example, you can search only for calendar items or contacts. Here's a screenshot of the different message types you can search for; the default is to search for all message types. 
  
    Click **Next** when you've completed the **Search query** page. 
    
10. <span data-ttu-id="c4b8c-p112">En la página **configuración de retención en contexto** , haga clic en **Finalizar** para iniciar la búsqueda. Para recuperar el correo electrónico eliminado, no hay ningún motivo para colocar el buzón del usuario en suspensión.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-p112">On the **In-Place Hold settings** page, click **Finish** to start the search. To recover deleted email, there's no reason to place the user's mailbox on hold.</span></span> 
    
    <span data-ttu-id="c4b8c-181">Después de iniciar la búsqueda, Exchange mostrará una estimación del tamaño total y el número de elementos que será devuelto por la búsqueda en función de los criterios especificados.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-181">After you start the search, Exchange will display an estimate of the total size and number of items that will be returned by the search based on the criteria you specified.</span></span>
    
11. <span data-ttu-id="c4b8c-p113">Seleccione la búsqueda que acaba de crear y haga clic en **Actualizar**![actualizar](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) para actualizar la información que se muestra en el panel de detalles. El estado de **Estimación se ha realizado correctamente** indica que la búsqueda ha finalizado. Exchange también muestra una estimación del número total de elementos (y su tamaño) que se encuentra por la búsqueda en función de los criterios de búsqueda que se especificó en el paso 9.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-p113">Select the search you just created and click **Refresh**![refresh](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) to update the information displayed in the details pane. The status of **Estimate Succeeded** indicates that the search has finished. Exchange also displays an estimate of the total number of items (and their size) found by the search based on the search criteria you specified in step 9.</span></span> 
    
12. <span data-ttu-id="c4b8c-p114">En el panel de detalles, haga clic en **vista previa de resultados de búsqueda** para ver los elementos que se han encontrado. Esto puede ayudar a identificar los elementos que está buscando. Si encuentra el elemento o elementos que se intenta recuperar, vaya al paso 4 para exportar los resultados de búsqueda a un archivo PST.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-p114">In the details pane, click **Preview search results** to view the items that were found. This might help you identify the item(s) that you're looking for. If you find the item(s) you're trying to recover, go to step 4 to export the search results to a PST file.</span></span> 
    
    ![Haga clic en vista previa de resultados de búsqueda para ver el elemento que está intentando recuperar](media/a2cea921-dafa-45d6-97d4-ae45a226b8d3.png)
  
13. <span data-ttu-id="c4b8c-p115">Si no encuentra lo busca, puede revisar los criterios de búsqueda mediante la selección de la búsqueda, haga clic en **Editar**![icono Editar](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif)y, a continuación, haga clic en **consulta de búsqueda**. Cambiar los criterios de búsqueda y, a continuación, vuelva a ejecutar la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-p115">If you don't find what you're looking for, you can revise your search criteria by selecting the search, clicking **Edit**![Edit icon](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif), and then clicking **Search query**. Change the search criteria and then rerun the search.</span></span>
    
[<span data-ttu-id="c4b8c-191">Return to top</span><span class="sxs-lookup"><span data-stu-id="c4b8c-191">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="optional-step-3-copy-the-search-results-to-a-discovery-mailbox"></a><span data-ttu-id="c4b8c-192">(Opcional) Paso 3: Copiar los resultados de búsqueda en un buzón de detección</span><span class="sxs-lookup"><span data-stu-id="c4b8c-192">(Optional) Step 3: Copy the search results to a discovery mailbox</span></span>
<span data-ttu-id="c4b8c-193"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="c4b8c-193"></span></span>

<span data-ttu-id="c4b8c-p116">Si no puede encontrar un elementos por obtener una vista previa de los resultados de búsqueda o si desea ver los elementos que están en la carpeta del usuario elementos recuperables, a continuación, puede copiar los resultados de búsqueda en un buzón especial (denominado un buzón de detección) y, a continuación, abra ese buzón de correo en Outlook en el web t o ver los elementos reales. El mejor motivo para copiar los resultados de búsqueda es por lo que puede ver los elementos en la carpeta del usuario elementos recuperables. Más probable es que el elemento que está intentando recuperar se encuentra en la subcarpeta de purga.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-p116">If you can't find an items by previewing the search results or if you want to see which items are in the user's Recoverable Items folder, then you can copy the search results to a special mailbox (called a discovery mailbox) and then open that mailbox in Outlook on the web to view the actual items. The best reason to copy the search results is so you can view the items in the user's Recoverable Items folder. More than likely, the item you're trying to recover is located in the Purges subfolder.</span></span> 
  
1. <span data-ttu-id="c4b8c-197">En el centro de administración de Exchange, vaya a **administración de cumplimiento** \> **exhibición de documentos electrónicos en contexto &amp; suspensión**.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-197">In the Exchange admin center, go to **Compliance management** \> **In-Place eDiscovery &amp; Hold**.</span></span>
    
2. <span data-ttu-id="c4b8c-198">En la lista de búsquedas, seleccione la búsqueda que creó en el paso 2.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-198">In the list of searches, select the search that you created in Step 2.</span></span>
    
3. <span data-ttu-id="c4b8c-199">Haga clic en **búsqueda**![búsqueda](media/c94e8591-7044-4650-a0d1-c57c0633ab4f.png)y, a continuación, haga clic en **copiar los resultados de búsqueda** de la lista desplegable.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-199">Click **Search**![search](media/c94e8591-7044-4650-a0d1-c57c0633ab4f.png), and then click **Copy search results** from the drop-down list.</span></span> 
    
    ![Haga clic en Buscar y, a continuación, haga clic en copiar los resultados de búsqueda](media/7888df82-94b4-4e44-8a53-f66854dc7c86.png)
  
4. <span data-ttu-id="c4b8c-201">En la página **Copiar los resultados de búsqueda** , haga clic en **Examinar**.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-201">On the **Copy Search Results** page, click **Browse**.</span></span>
    
    ![Deje las casillas de verificación no está seleccionada cuando la recuperación de elementos eliminados](media/37f27999-a5b2-4fed-87e2-bad6dc23cdae.png)
  
5. <span data-ttu-id="c4b8c-203">En **Nombre para mostrar**, haga clic en **El buzón de correo de detección de búsqueda**y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-203">Under **Display Name**, click **Discovery Search Mailbox**, and then click **OK**.</span></span>
    
    ![Copiar los resultados de búsqueda en el buzón de búsqueda de detección predeterminado](media/36e8ef47-0035-4982-9ed6-426719c5f9ec.png)
  
    > [!NOTE]
    > <span data-ttu-id="c4b8c-205">El buzón de búsqueda de detección es un buzón de correo de detección predeterminado que se crea automáticamente en la organización de Office 365.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-205">The Discovery Search Mailbox is a default discovery mailbox that is automatically created in your Office 365 organization.</span></span> 
  
6. <span data-ttu-id="c4b8c-206">Copia en la página **Copiar los resultados de búsqueda** , haga clic en **Copiar** para iniciar el proceso para copiar los resultados de búsqueda en el buzón de búsqueda de detección.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-206">Back on the **Copy Search Results** page, click **Copy** to start the process to copy the search results to the Discovery Search Mailbox.</span></span> 
    
    ![Haga clic en Copiar para copiar los resultados de búsqueda en el buzón de búsqueda de detección](media/71307a9d-f7a1-4e01-ae37-1d49040cc3fd.png)
  
7. <span data-ttu-id="c4b8c-208">Haga clic en **Actualizar**![actualizar](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) para actualizar la información sobre el estado de copia que se muestra en el panel de detalles.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-208">Click **Refresh**![refresh](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) to update the information about the copying status that is displayed in the details pane.</span></span> 
    
8. <span data-ttu-id="c4b8c-209">Cuando se complete la copia, haga clic en **Abrir** para abrir el buzón de búsqueda de detección para ver los resultados de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-209">When the copying is complete, click **Open** to open the Discovery Search Mailbox to view the search results.</span></span> 
    
    ![Haga clic en Abrir para ir al buzón de búsqueda de detección para ver los resultados de búsqueda](media/6cc81e0f-ceed-4464-9040-79b6f920de35.png)
  
    <span data-ttu-id="c4b8c-p117">Los resultados de búsqueda que se copian en el buzón de búsqueda de detección se colocan en una carpeta que tiene el mismo nombre que la búsqueda de exhibición de documentos electrónicos en contexto. Puede hacer clic en una carpeta para mostrar los elementos de esa carpeta.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-p117">The search results copied to the Discovery Search Mailbox are placed in a folder that has the same name as the In-Place eDiscovery search. You can click a folder to display the items in that folder.</span></span>
    
    ![Resultados de búsqueda en el buzón de correo de la búsqueda de detección; sólo se pueden recuperar los elementos de la carpeta de purga por un administrador](media/2ef8e5fb-3e63-4f62-938e-307efe9f6998.gif)
  
    <span data-ttu-id="c4b8c-p118">Cuando se ejecuta una búsqueda, también se busca en la carpeta del usuario elementos recuperables. Esto significa que si los elementos de la carpeta elementos recuperables cumplen los criterios de búsqueda, se incluyen en los resultados de búsqueda. Elementos de la carpeta de eliminaciones son los elementos que el usuario eliminado de forma permanente (mediante la eliminación de un elemento desde la carpeta Elementos eliminados o seleccionándolo y presionando la tecla **MAYÚS + SUPR**. Un usuario puede usar la herramienta de recuperar elementos eliminados en Outlook o Outlook en la web para recuperar los elementos en la carpeta de eliminaciones. Elementos de la carpeta de purga son los elementos que el usuario se purga mediante la herramienta de recuperar elementos eliminados o elementos que se han purgado automáticamente por una directiva aplicada al buzón. En cualquier caso, sólo un administrador puede recuperar los elementos en la carpeta de purga.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-p118">When you run a search, the user's Recoverable Items folder is also searched. That means if items in the Recoverable Items folder meet the search criteria, they are included in the search results. Items in the Deletions folder are items that the user permanently deleted (by deleting an item from the Deleted Items folder or by selecting it and pressing **Shift+Delete**. A user can use the Recover Deleted Items tool in Outlook or Outlook on the web to recover items in the Deletions folder. Items in the Purges folder are items that the user purged by using the Recover Deleted Items tool or items they were automatically purged by a policy applied to the mailbox. In either case, only an admin can recover items in the Purges folder.</span></span> 
    
    > [!TIP]
    > <span data-ttu-id="c4b8c-p119">Si un usuario no puede encontrar un elemento eliminado mediante la herramienta de elementos recuperables, pero sigue siendo recuperable que el elemento (lo que significa no haya sido eliminado con permanentemente desde el buzón de correo), lo más probable es que está en la carpeta de purga. Por lo tanto, asegúrese de buscar en la carpeta de purga para el elemento eliminado que está intentando recuperar para un usuario.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-p119">If a user can't find a deleted item using the Recoverable Items tool, but that item is still recoverable (meaning that it hasn't been permanently removed from the mailbox), it's more than likely located in the Purges folder. So, be sure to look in the Purges folder for the deleted item you're trying to recover for a user.</span></span> 
  
[<span data-ttu-id="c4b8c-222">Return to top</span><span class="sxs-lookup"><span data-stu-id="c4b8c-222">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-4-export-the-search-results-to-a-pst-file"></a><span data-ttu-id="c4b8c-223">Paso 4: Exportar los resultados de búsqueda a un archivo PST</span><span class="sxs-lookup"><span data-stu-id="c4b8c-223">Step 4: Export the search results to a PST file</span></span>
<span data-ttu-id="c4b8c-224"><a name="step4"> </a></span><span class="sxs-lookup"><span data-stu-id="c4b8c-224"></span></span>

<span data-ttu-id="c4b8c-p120">Una vez que encuentre el elemento que está intentando recuperar para un usuario, el siguiente paso es exportar los resultados de la búsqueda que ejecutó en el paso 2 a un archivo PST. El usuario utilizará este archivo PST en el paso siguiente para restaurar el elemento eliminado en su buzón.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-p120">After you find the item you're trying to recover for a user, the next step is to export the results from the search you ran in Step 2 to a PST file. The user will use this PST file in the next step to restore the deleted item to their mailbox.</span></span>
  
1. <span data-ttu-id="c4b8c-227">En el centro de administración de Exchange, vaya a **administración de cumplimiento** \> **exhibición de documentos electrónicos en contexto &amp; suspensión**.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-227">In the Exchange admin center, go to **Compliance management** \> **In-Place eDiscovery &amp; Hold**.</span></span>
    
2. <span data-ttu-id="c4b8c-228">En la lista de búsquedas, seleccione la búsqueda que creó en el paso 2.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-228">In the list of searches, select the search that you created in Step 2.</span></span>
    
3. <span data-ttu-id="c4b8c-229">Haga clic en **Exportar a un archivo PST**.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-229">Click **Export to a PST file**.</span></span>
    
    ![Haga clic en Exportar a un archivo PST](media/4e59ae17-4541-43f4-a6d1-1f8b9ba9404b.png)
  
4. <span data-ttu-id="c4b8c-231">Si le pide para instalar la herramienta de exportación de exhibición de documentos, haga clic en **Ejecutar**.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-231">If you're prompted to install the eDiscovery Export Tool, click **Run**.</span></span>
    
5. <span data-ttu-id="c4b8c-232">En la herramienta de exportación de PST de eDiscovery, haga clic en **Examinar** para especificar la ubicación donde desea descargar el archivo PST.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-232">In the eDiscovery PST Export Tool, click **Browse** to specify the location where you want to download the PST file.</span></span> 
    
    ![La herramienta de exportación de PST de exhibición de documentos electrónicos](media/17274d27-992e-4034-8133-8f793f554e6c.png)
  
    <span data-ttu-id="c4b8c-234">Puede pasar por alto las opciones para habilitar la desduplicación e incluir buscar elementos.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-234">You can ignore the options to enable deduplication and include unsearchable items.</span></span>
    
6. <span data-ttu-id="c4b8c-235">Haga clic en **Iniciar** para descargar el archivo PST en el equipo.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-235">Click **Start** to download the PST file to your computer.</span></span> 
    
    <span data-ttu-id="c4b8c-p121">La **herramienta de exportación de PST de exhibición de documentos** muestra información de estado sobre el proceso de exportación. Una vez finalizada la exportación, se puede tener acceso al archivo en la ubicación donde descargó.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-p121">The **eDiscovery PST Export Tool** displays status information about the export process. When the export is complete, you can access the file in the location where it was downloaded.</span></span> 
    
[<span data-ttu-id="c4b8c-238">Return to top</span><span class="sxs-lookup"><span data-stu-id="c4b8c-238">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-5-restore-the-recovered-items-to-the-users-mailbox"></a><span data-ttu-id="c4b8c-239">Paso 5: Restaurar los elementos recuperados en el buzón del usuario</span><span class="sxs-lookup"><span data-stu-id="c4b8c-239">Step 5: Restore the recovered items to the user's mailbox</span></span>
<span data-ttu-id="c4b8c-240"><a name="step5"> </a></span><span class="sxs-lookup"><span data-stu-id="c4b8c-240"></span></span>

<span data-ttu-id="c4b8c-p122">El último paso es usar el archivo PST que se exportó en el paso 4 para restaurar los elementos recuperados en el buzón del usuario. Después de enviar el archivo PST al usuario, en el resto de este paso se realiza por el usuario para abrir el archivo PST y, a continuación, mover los elementos recuperados a otra carpeta en su buzón. Para obtener instrucciones paso a paso, también puede enviar al usuario un vínculo para este tema: [Abrir y cerrar archivos de datos de Outlook (.pst)](https://support.office.com/article/381b776d-7511-45a0-953a-0935c79d24f2). O bien, puede enviar al usuario un vínculo a la sección [restaurar los elementos a un buzón mediante un archivo PST eliminados](recover-deleted-items-in-a-mailbox.md#restoredeleteditems) más adelante y pídales que lleve a cabo estos pasos.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-p122">The final step is to use the PST file that was exported in step 4 to restore the recovered items to the user's mailbox. After you send the PST file to the user, the remainder of this step is performed by the user to open the PST file and then move the recovered items to another folder in their mailbox. For step-by-step instructions, you can also send the user a link to this topic: [Open and close Outlook Data Files (.pst)](https://support.office.com/article/381b776d-7511-45a0-953a-0935c79d24f2). Or you can send the user a link to the [Restore deleted items to a mailbox using a PST file](recover-deleted-items-in-a-mailbox.md#restoredeleteditems) section below and ask them to perform these steps.</span></span> 
  
 <span data-ttu-id="c4b8c-245">**Enviar el archivo PST al usuario**</span><span class="sxs-lookup"><span data-stu-id="c4b8c-245">**Send the PST file to the user**</span></span>
  
<span data-ttu-id="c4b8c-p123">El paso final que necesita para llevar a cabo está enviando el archivo PST que se exportó en el paso 4 para el usuario. Hay varias formas de hacer esto:</span><span class="sxs-lookup"><span data-stu-id="c4b8c-p123">The final step that you need to perform is sending the PST file that was exported in step 4 to the user. There are a few ways to do this:</span></span>
  
- <span data-ttu-id="c4b8c-p124">Adjunte el archivo PST a un mensaje de correo electrónico. Si Outlook está configurado para los archivos PST de bloque, tendrá el archivo zip y, a continuación, se adjunta al mensaje. Aquí es cómo:</span><span class="sxs-lookup"><span data-stu-id="c4b8c-p124">Attach the PST file to an email message. If Outlook is configured to block PST files, then you will have to zip the file and then attach it to the message. Here's how:</span></span>
    
1. <span data-ttu-id="c4b8c-251">En el Explorador de Windows o el Explorador de archivos, busque el archivo PST.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-251">In Windows Explorer or File Explorer, browse to the PST file.</span></span>
    
2. <span data-ttu-id="c4b8c-p125">Haga clic en el archivo y, a continuación, seleccione **Enviar a** \> **carpeta comprimida (zip)**. Windows crea un nuevo archivo zip y se le da un nombre idéntico como el archivo PST.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-p125">Right-click the file, and then select **Send to** \> **Compressed (zipped) folder**. Windows creates a new zip file and gives it an identical name as the PST file.</span></span>
    
3. <span data-ttu-id="c4b8c-254">Adjuntar el archivo comprimido de PST a un mensaje de correo electrónico y enviarlo al usuario, que, a continuación, puede descomprimir el archivo haciendo clic en él.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-254">Attach the compressed PST file to an email message and send it to the user, who can then decompress the file just by clicking it.</span></span>
    
- <span data-ttu-id="c4b8c-255">Copie el archivo PST en una carpeta compartida que el usuario puede tener acceso y recuperarlo.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-255">Copy the PST file to a shared folder that the user can access and retrieve it.</span></span>
    
<span data-ttu-id="c4b8c-256">Los pasos descritos en la siguiente sección se realizan por el usuario para restaurar los elementos eliminados en su buzón.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-256">The steps in the next section are performed by the user to restore the deleted items to their mailbox.</span></span>
  
 <span data-ttu-id="c4b8c-257">**Restaurar los elementos eliminados en un buzón con un archivo PST**</span><span class="sxs-lookup"><span data-stu-id="c4b8c-257">**Restore deleted items to a mailbox using a PST file**</span></span>
  
<span data-ttu-id="c4b8c-p126">Se debe usar la aplicación de escritorio de Outlook para restaurar un elemento eliminado mediante un archivo PST. No puede usar Outlook Web App o Outlook en la web para abrir un archivo PST.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-p126">You have to use the Outlook desktop app to restore a deleted item by using a PST file. You can't use Outlook Web App or Outlook on the web to open a PST file.</span></span>
  
1. <span data-ttu-id="c4b8c-260">En Outlook 2013 o 2016 de Outlook, haga clic en la pestaña **archivo** .</span><span class="sxs-lookup"><span data-stu-id="c4b8c-260">In Outlook 2013 or Outlook 2016, click the **File** tab.</span></span> 
    
2. <span data-ttu-id="c4b8c-261">Haga clic en **abiertos &amp; exportar**y, a continuación, haga clic en **Abrir archivo de datos de Outlook**.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-261">Click **Open &amp; Export**, and then click **Open Outlook Data File**.</span></span>
    
3. <span data-ttu-id="c4b8c-262">Vaya a la ubicación donde guardó el archivo PST que envían el administrador.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-262">Browse to the location where you saved the PST file that your administrator sent.</span></span>
    
4. <span data-ttu-id="c4b8c-263">Seleccione el archivo PST y, a continuación, haga clic en **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-263">Select the PST and then click **Open**.</span></span>
    
    <span data-ttu-id="c4b8c-264">El archivo PST aparece en la barra de navegación de la izquierda en Outlook.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-264">The PST file appears in the left-nav bar in Outlook.</span></span>
    
    ![El archivo PST aparece en la barra de navegación de la izquierda en Outlook](media/c9389392-d08a-4aa7-848c-4986d448b0f2.png)
  
5. <span data-ttu-id="c4b8c-266">Haga clic en las flechas para expandir el archivo PST y las carpetas debajo de él para buscar el elemento que desea recuperar.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-266">Click the arrows to expand the PST file and the folders under it to locate the item you want to recover.</span></span>
    
    ![Buscar en la carpeta de purga para el elemento que desea recuperar](media/d4e372d9-ac23-4e95-8639-d8da690fefa7.png)
  
    > [!TIP]
    > <span data-ttu-id="c4b8c-p127">Buscar en la carpeta de purga para el elemento que desea recuperar. Esto es una carpeta oculta que purgarán se mueven los elementos a. Es probable que es el elemento que se encuentra el administrador recuperado en esta carpeta.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-p127">Look in the Purges folder for the item you want to recover. This is a hidden folder that purged items are moved to. It's likely the item that your administrator recovered is in this folder.</span></span> 
  
6. <span data-ttu-id="c4b8c-271">Haga clic en el elemento que desea recuperar y, a continuación, haga clic en **mover** \> **Otra carpeta**.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-271">Right-click the item you want to recover and then click **Move** \> **Other Folder**.</span></span>
    
    ![Haga clic en mover y, a continuación, seleccionar otra carpeta](media/090063df-2aa0-444a-8e47-abd6fe6cf7a8.png)
  
7. <span data-ttu-id="c4b8c-273">Para mover el elemento a la Bandeja de entrada, haga clic en la **Bandeja de entrada**y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-273">To move the item to your inbox, click **Inbox**, and then click **OK**.</span></span>
    
    <span data-ttu-id="c4b8c-274">**Sugerencia:** Para recuperar otros tipos de elementos, realice una de las siguientes opciones:</span><span class="sxs-lookup"><span data-stu-id="c4b8c-274">**Tip:** To recover other types of items, do one of the following:</span></span> 
    
  - <span data-ttu-id="c4b8c-275">Para recuperar un elemento de calendario, haga clic en él y, a continuación, haga clic en **mover** \> **Otra carpeta** \> **calendario**.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-275">To recover a calendar item, right-click it, and then click **Move** \> **Other Folder** \> **Calendar**.</span></span>
    
  - <span data-ttu-id="c4b8c-276">Para recuperar un contacto, haga clic en él y, a continuación, haga clic en **mover** \> **Otra carpeta** \> **contactos**.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-276">To recover a contact, right-click it, and then click **Move** \> **Other Folder** \> **Contacts**.</span></span>
    
  - <span data-ttu-id="c4b8c-277">Para recuperar una tarea, haga clic en él y, a continuación, haga clic en **mover** \> **Otra carpeta** \> **tareas**.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-277">To recover a task, right-click it, and then click **Move** \> **Other Folder** \> **Tasks**.</span></span>
    
![Seleccione una carpeta para mover otros tipos de elementos](media/f8290131-43f2-46f1-bc07-228c2d83b96c.png)
  
    Note that calendar items, contacts, and tasks are located directly in the Purges folder, and not in a Calendar, Contacts, or Tasks subfolder. However, you can sort by **Type** to group similar types of items. 
    
8. <span data-ttu-id="c4b8c-279">Cuando haya terminado de recuperación de elementos eliminados, haga clic en el archivo PST en la barra de navegación de la izquierda y seleccione **Cerrar "nombre del archivo PST"**.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-279">When you're finished recovering deleted items, right-click the PST file in the left-nav bar and select **Close "name of PST file"**.</span></span>
    
[<span data-ttu-id="c4b8c-280">Return to top</span><span class="sxs-lookup"><span data-stu-id="c4b8c-280">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="more-information"></a><span data-ttu-id="c4b8c-281">Más información</span><span class="sxs-lookup"><span data-stu-id="c4b8c-281">More information</span></span>
<span data-ttu-id="c4b8c-282"><a name="moreinfo"> </a></span><span class="sxs-lookup"><span data-stu-id="c4b8c-282"></span></span>

- <span data-ttu-id="c4b8c-p128">Es posible que un usuario recuperar un elemento eliminado de forma permanente si no ha caducado el período de retención de elementos eliminados para el elemento. Como administrador, es posible que deba especificados cuánto tiempo los elementos en la carpeta elementos recuperables están disponibles para la recuperación. Por ejemplo, puede haber una directiva que elimina cualquier cosa que ha sido en la carpeta Elementos eliminados de un usuario para 30 días y otra directiva que permite a los usuarios recuperar los elementos en la carpeta elementos recuperables hasta otro 14 días. Sin embargo, después de este 14 días, es posible que aún podrá recuperar un elemento en el buzón del usuario mediante los procedimientos descritos en este tema.</span><span class="sxs-lookup"><span data-stu-id="c4b8c-p128">It might be possible for a user to recover a permanently deleted item if the deleted item retention period for the item hasn't expired. As an admin you may have specified how long items in the Recoverable Items folder are available for recovery. For example, there might be a policy that deletes anything that's been in a user's Deleted Items folder for 30 days, and another policy that lets users recover items in the Recoverable Items folder for up to another 14 days. However, after this 14 days, you may still be able to recover an item in a user's mailbox by using the procedures in this topic.</span></span>
    
- <span data-ttu-id="c4b8c-p129">Los usuarios pueden recuperar un elemento eliminado si no ha purgado y si no ha caducado el período de retención de elementos eliminados de ese elemento. Para ayudar a los usuarios recuperar elementos eliminados en sus buzones de correo, elija a uno de los siguientes temas:</span><span class="sxs-lookup"><span data-stu-id="c4b8c-p129">Users can recover a deleted item if it hasn't been purged and if the deleted item retention period for that item hasn't expired. To help users recover deleted items in their mailbox, point them to one of the following topics:</span></span>
    
  - [<span data-ttu-id="c4b8c-289">Recuperación de elementos eliminados en Outlook para Windows</span><span class="sxs-lookup"><span data-stu-id="c4b8c-289">Recover deleted items in Outlook for Windows</span></span>](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
    
  - [<span data-ttu-id="c4b8c-290">Recuperar elementos eliminados en Outlook 2010</span><span class="sxs-lookup"><span data-stu-id="c4b8c-290">Recover deleted items in Outlook 2010</span></span>](https://support.office.com/article/cd9dfe12-8e8c-4a21-bbbf-4bd103a3f1fe)
    
  - [<span data-ttu-id="c4b8c-291">Recuperar elementos eliminados o correo electrónico en Outlook Web App</span><span class="sxs-lookup"><span data-stu-id="c4b8c-291">Recover deleted items or email in Outlook Web App</span></span>](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
    
  - [<span data-ttu-id="c4b8c-292">Restauración de los mensajes de correo electrónico eliminados en Outlook en el web</span><span class="sxs-lookup"><span data-stu-id="c4b8c-292">Restore deleted email messages in Outlook on the web</span></span>](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
    
  - [<span data-ttu-id="c4b8c-293">Recuperación de un contacto eliminado en Outlook</span><span class="sxs-lookup"><span data-stu-id="c4b8c-293">Recover a deleted contact in Outlook</span></span>](https://support.office.com/article/51c83288-6888-4dcd-8c99-4932daabf643)
    
  - [<span data-ttu-id="c4b8c-294">Restauración de los mensajes de correo electrónico eliminados en Outlook.com</span><span class="sxs-lookup"><span data-stu-id="c4b8c-294">Restore deleted email messages in Outlook.com</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=623435)
    
[<span data-ttu-id="c4b8c-295">Return to top</span><span class="sxs-lookup"><span data-stu-id="c4b8c-295">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  

