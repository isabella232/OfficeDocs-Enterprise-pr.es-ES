---
title: Recuperar elementos eliminados en un buzón de usuario. Ayuda para administradores
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 6/29/2018
audience: Admin
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
description: 'Este artículo está destinado a los administradores. ¿Un usuario elimina permanentemente los elementos de su buzón de Outlook? El usuario desea volver a hacerlo, pero no puede recuperarlos. Es posible que pueda recuperar los elementos purgados si no se han quitado permanentemente del buzón de correo del usuario. '
ms.openlocfilehash: d4be48d6166d970572dd1cb343ccd83f22330e12
ms.sourcegitcommit: b4c82c0bf61f50386e534ad23479b5cf84f4e2ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2019
ms.locfileid: "35203659"
---
<a name="__top"></a>
# <a name="recover-deleted-items-in-a-user-mailbox---admin-help"></a><span data-ttu-id="3857d-106">Recuperar elementos eliminados en un buzón de usuario. Ayuda para administradores</span><span class="sxs-lookup"><span data-stu-id="3857d-106">Recover deleted items in a user mailbox - Admin Help</span></span>

<span data-ttu-id="3857d-107">**Este artículo está destinado a los administradores. ¿Está tratando de recuperar elementos eliminados en su propio buzón?**</span><span class="sxs-lookup"><span data-stu-id="3857d-107">**This article is for administrators. Are you trying to recover deleted items in your own mailbox?**</span></span> <span data-ttu-id="3857d-108">Pruebe con uno de los siguientes procedimientos:</span><span class="sxs-lookup"><span data-stu-id="3857d-108">Try one of the following:</span></span>
- [<span data-ttu-id="3857d-109">Recuperación de elementos eliminados en Outlook para Windows</span><span class="sxs-lookup"><span data-stu-id="3857d-109">Recover deleted items in Outlook for Windows</span></span>](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
- [<span data-ttu-id="3857d-110">Recuperar elementos eliminados o correo electrónico en Outlook Web App</span><span class="sxs-lookup"><span data-stu-id="3857d-110">Recover deleted items or email in Outlook Web App</span></span>](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
- [<span data-ttu-id="3857d-111">Restaurar mensajes de correo electrónico eliminados en Outlook en la web</span><span class="sxs-lookup"><span data-stu-id="3857d-111">Restore deleted email messages in Outlook on the web</span></span>](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
- [<span data-ttu-id="3857d-112">Outlook.com</span><span class="sxs-lookup"><span data-stu-id="3857d-112">Outlook.com</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=623435)
   
<span data-ttu-id="3857d-113">¿Un usuario elimina permanentemente los elementos de su buzón de Outlook?</span><span class="sxs-lookup"><span data-stu-id="3857d-113">Did a user permanently delete items from their Outlook mailbox?</span></span> <span data-ttu-id="3857d-114">El usuario desea volver a hacerlo, pero no puede recuperarlos.</span><span class="sxs-lookup"><span data-stu-id="3857d-114">The user wants them back but can't recover them.</span></span> <span data-ttu-id="3857d-115">Es posible que pueda recuperar los elementos purgados si no se han quitado permanentemente del buzón de correo del usuario.</span><span class="sxs-lookup"><span data-stu-id="3857d-115">You may be able recover the purged items if they haven't been permanently removed from the user's mailbox.</span></span> <span data-ttu-id="3857d-116">Para ello, use la herramienta de exhibición de documentos electrónicos local en Exchange Online para buscar correos electrónicos eliminados y otros elementos (como contactos, citas del calendario y tareas) en el buzón de un usuario.</span><span class="sxs-lookup"><span data-stu-id="3857d-116">You do this by using the In-Place eDiscovery tool in Exchange Online to search for deleted email and other items—and such as contacts, calendar appointments, and tasks—in a user's mailbox.</span></span> <span data-ttu-id="3857d-117">Si encuentra los elementos eliminados, puede exportarlos a un archivo PST (también denominado archivo de datos de Outlook), que el usuario puede usar para restaurar los elementos de nuevo en su buzón.</span><span class="sxs-lookup"><span data-stu-id="3857d-117">If you find the deleted items, you can export them to a PST file (also called an Outlook Data File), which the user can then use to restore the items back to their mailbox.</span></span>
  
<span data-ttu-id="3857d-118">Estos son los pasos para recuperar los elementos eliminados en el buzón de un usuario.</span><span class="sxs-lookup"><span data-stu-id="3857d-118">Here are the steps for recovering deleted items in a user's mailbox.</span></span> <span data-ttu-id="3857d-119">¿Cuánto tiempo se tardará?</span><span class="sxs-lookup"><span data-stu-id="3857d-119">How long will this take?</span></span> <span data-ttu-id="3857d-120">La primera vez puede tardar 20 o 30 minutos en completar todos los pasos, en función de cuántos elementos esté intentando recuperar.</span><span class="sxs-lookup"><span data-stu-id="3857d-120">The first time might take 20 or 30 minutes to complete all the steps, depending on how many items you're trying to recover.</span></span>
  
> [!NOTE]
> <span data-ttu-id="3857d-121">Debe ser **Administrador de Exchange** o **Administrador Global** de Office 365 o ser miembro del grupo de roles de administración de la organización en Exchange Online para realizar los pasos descritos en este artículo.</span><span class="sxs-lookup"><span data-stu-id="3857d-121">You have to be an **Exchange administrator** or **Global administrator** in Office 365 or be a member of the Organization Management role group in Exchange Online to perform the steps in this article.</span></span> <span data-ttu-id="3857d-122">Para obtener más información, vea [Información sobre los roles de administrador de Office 365](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span><span class="sxs-lookup"><span data-stu-id="3857d-122">For more information, see [About Office 365 admin roles](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span></span> 
  
## <a name="step-1-assign-yourself-ediscovery-permissions"></a><span data-ttu-id="3857d-123">Paso 1: asignar permisos de exhibición de documentos electrónicos</span><span class="sxs-lookup"><span data-stu-id="3857d-123">Step 1: Assign yourself eDiscovery permissions</span></span>
<span data-ttu-id="3857d-124"><a name="step1"> </a></span><span class="sxs-lookup"><span data-stu-id="3857d-124"></span></span>

<span data-ttu-id="3857d-125">El primer paso es asignarse a sí mismo los permisos necesarios en Exchange Online para poder usar la herramienta de exhibición de documentos electrónicos local para buscar en el buzón de correo de un usuario.</span><span class="sxs-lookup"><span data-stu-id="3857d-125">The first step is to assign yourself the necessary permissions in Exchange Online so you can use the In-Place eDiscovery tool to search a user's mailbox.</span></span> <span data-ttu-id="3857d-126">Solo tiene que hacer esto una vez.</span><span class="sxs-lookup"><span data-stu-id="3857d-126">You only have to do this once.</span></span> <span data-ttu-id="3857d-127">Si tiene que buscar en otro buzón de correo en el futuro, puede omitir este paso.</span><span class="sxs-lookup"><span data-stu-id="3857d-127">If you have to search another mailbox in the future, you can skip this step.</span></span>
  
1. <span data-ttu-id="3857d-128">[Where to sign in to Office 365 for business](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) con su cuenta profesional o educativa.</span><span class="sxs-lookup"><span data-stu-id="3857d-128">[Where to sign in to Office 365 for business](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) with your work or school account.</span></span> 
    
2. <span data-ttu-id="3857d-129">Seleccione el icono ![del iniciador de aplicaciones el icono del iniciador de aplicaciones de Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) en la esquina superior izquierda y haga clic en **Administrador**.</span><span class="sxs-lookup"><span data-stu-id="3857d-129">Select the app launcher icon ![The app launcher icon in Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) in the upper-left and click **Admin**.</span></span>
    
3. <span data-ttu-id="3857d-130">En el panel de navegación izquierdo del centro de administración de Office 365, expanda **centros de administración**y, a continuación, haga clic en **Exchange**.</span><span class="sxs-lookup"><span data-stu-id="3857d-130">In the left navigation in the Office 365 admin center, expand **Admin centers**, and then click **Exchange**.</span></span>
    
    ![Lista del centro de administración](media/7d308eb7-ba63-4156-a845-3770facc5de4.PNG)
  
4. <span data-ttu-id="3857d-132">En el centro de administración de Exchange, haga clic en **permisos**y, a continuación, en **roles de administrador**.</span><span class="sxs-lookup"><span data-stu-id="3857d-132">In the Exchange admin center, click **Permissions**, and then click **Admin roles**.</span></span>
    
5. <span data-ttu-id="3857d-133">En la vista de lista, **Seleccione Administración de detección**y, a continuación, haga clic en **Editar**![icono](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif)de edición.</span><span class="sxs-lookup"><span data-stu-id="3857d-133">In the list view, select **Discovery Management**, and then click **Edit**![Edit icon](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif).</span></span>
    
    ![Agregarse al grupo de roles de administración de detección en el EAC](media/e5c98e93-d6a0-40c5-a143-bac956eedaa7.png)
  
6. <span data-ttu-id="3857d-135">En **grupo de roles**, **en miembros**, haga clic en](media/8ee52980-254b-440b-99a2-18d068de62d3.gif) **Agregar**![icono de agregar.</span><span class="sxs-lookup"><span data-stu-id="3857d-135">In **Role Group**, under **Members**, click **Add**![Add icon](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
7. <span data-ttu-id="3857d-136">En **seleccionar miembros**, seleccione usted en la lista de nombres, haga clic en **Agregar**y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="3857d-136">In **Select Members**, select yourself from the list of names, click **Add**, and then click **OK**.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="3857d-137">También puede Agregar un grupo del que sea miembro, como administración de la organización o TenantAdmins.</span><span class="sxs-lookup"><span data-stu-id="3857d-137">You can also add a group that you are a member of, such as Organization Management or TenantAdmins.</span></span> <span data-ttu-id="3857d-138">Si agrega un grupo, se asignará a otros miembros del grupo los permisos necesarios para ejecutar la herramienta de exhibición de documentos electrónicos local.</span><span class="sxs-lookup"><span data-stu-id="3857d-138">If you add a group, other members of the group will be assigned the necessary permissions to run the In-Place eDiscovery tool.</span></span> 
  
8. <span data-ttu-id="3857d-139">En **grupo de roles**, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="3857d-139">In **Role Group**, click **Save**.</span></span>
    
9. <span data-ttu-id="3857d-140">Cierre la sesión de Office 365.</span><span class="sxs-lookup"><span data-stu-id="3857d-140">Sign out of Office 365.</span></span>
    
    <span data-ttu-id="3857d-141">Tiene que cerrar sesión antes de iniciar el siguiente paso para que se apliquen los nuevos permisos.</span><span class="sxs-lookup"><span data-stu-id="3857d-141">You have to sign out before you start the next step so the new permissions will take effect.</span></span>
    
> [!CAUTION]
> <span data-ttu-id="3857d-142">Los miembros del grupo de roles Discovery Management pueden tener acceso al contenido de mensajes confidenciales.</span><span class="sxs-lookup"><span data-stu-id="3857d-142">Members of the Discovery Management role group can access sensitive message content.</span></span> <span data-ttu-id="3857d-143">Esto incluye buscar en todos los buzones de la organización, obtener una vista previa de los resultados de la búsqueda (y otros elementos del buzón de correo), copiar los resultados en un buzón de correo de detección y exportar los resultados de la búsqueda a un archivo PST.</span><span class="sxs-lookup"><span data-stu-id="3857d-143">This includes searching all mailboxes in your organization, previewing the search results (and other mailbox items), copying the results to a discovery mailbox, and exporting the search results to a PST file.</span></span> 
  
[<span data-ttu-id="3857d-144">Return to top</span><span class="sxs-lookup"><span data-stu-id="3857d-144">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-2-search-the-users-mailbox-for-deleted-items"></a><span data-ttu-id="3857d-145">Paso 2: buscar en el buzón del usuario los elementos eliminados</span><span class="sxs-lookup"><span data-stu-id="3857d-145">Step 2: Search the user's mailbox for deleted items</span></span>
<span data-ttu-id="3857d-146"><a name="step2"> </a></span><span class="sxs-lookup"><span data-stu-id="3857d-146"></span></span>

<span data-ttu-id="3857d-147">Cuando se ejecuta una búsqueda de exhibición de documentos electrónicos local, la carpeta elementos recuperables del buzón en el que se realiza la búsqueda se incluye automáticamente en la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="3857d-147">When you run an In-Place eDiscovery search, the Recoverable Items folder in the mailbox that you search is automatically included in the search.</span></span> <span data-ttu-id="3857d-148">La carpeta elementos recuperables es donde se almacenan los elementos eliminados permanentemente hasta que se purgan (se quitan permanentemente) del buzón.</span><span class="sxs-lookup"><span data-stu-id="3857d-148">The Recoverable Items folder is where permanently deleted items are stored until they're purged (permanently removed) from the mailbox.</span></span> <span data-ttu-id="3857d-149">Por lo tanto, si no se ha purgado un elemento, debería poder encontrarlo mediante la herramienta de exhibición de documentos electrónicos local.</span><span class="sxs-lookup"><span data-stu-id="3857d-149">So, if an item hasn't been purged, you should be able to find it by using the In-Place eDiscovery tool.</span></span>
  
1. <span data-ttu-id="3857d-150">[Where to sign in to Office 365 for business](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) con su cuenta profesional o educativa.</span><span class="sxs-lookup"><span data-stu-id="3857d-150">[Where to sign in to Office 365 for business](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) with your work or school account.</span></span> 
    
2. <span data-ttu-id="3857d-151">Seleccione el icono ![del iniciador de aplicaciones el icono del iniciador de aplicaciones de Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) en la esquina superior izquierda y haga clic en **Administrador**.</span><span class="sxs-lookup"><span data-stu-id="3857d-151">Select the app launcher icon ![The app launcher icon in Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) in the upper-left and click **Admin**.</span></span>
    
3. <span data-ttu-id="3857d-152">En la navegación izquierda del centro de administración de Office 365, expanda **Administración**y, a continuación, haga clic en **Exchange**.</span><span class="sxs-lookup"><span data-stu-id="3857d-152">In the left navigation in the Office 365 admin center, expand **Admin**, and then click **Exchange**.</span></span>
    
4. <span data-ttu-id="3857d-153">En el centro de administración de Exchange, haga clic en **Administración de cumplimiento**, haga clic en **conservación de &amp; exhibición de**documentos electrónicos local y, a continuación, haga clic en **nuevo**![icono](media/8ee52980-254b-440b-99a2-18d068de62d3.gif)agregar.</span><span class="sxs-lookup"><span data-stu-id="3857d-153">In the Exchange admin center, click **Compliance management**, click **In-Place eDiscovery &amp; Hold**, and then click **New**![Add icon](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
    ![En la página Administración de cumplimiento de la EAC, haga clic en exhibición de documentos electrónicos local y retención.](media/9d9ff0f5-b9be-45b8-8b5e-6037a856b0a8.png)
  
5. <span data-ttu-id="3857d-155">En la página **nombre y descripción** , escriba un nombre para la búsqueda (por ejemplo, el nombre del usuario del que está recuperando el correo electrónico), una descripción opcional y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="3857d-155">On the **Name and description** page, type a name for the search (such as the name of the user you're recovering email for), an optional description, and then click **Next**.</span></span>
    
6. <span data-ttu-id="3857d-156">En la \*\*\*\* página buzones, haga clic en **especificar buzones para buscar**y, a continuación,](media/8ee52980-254b-440b-99a2-18d068de62d3.gif)haga clic en **Agregar**![icono de agregar.</span><span class="sxs-lookup"><span data-stu-id="3857d-156">On the **Mailboxes** page, click **Specify mailboxes to search**, and then click **Add**![Add icon](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
    ![Haga clic en especificar buzones para buscar en un buzón de manifiestan](media/83879a40-5e5c-49a8-be3b-c0023d197588.png)
  
7. <span data-ttu-id="3857d-158">Busque y seleccione el nombre del usuario para el que está recuperando el correo electrónico eliminado, haga clic en **Agregar**y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="3857d-158">Find and select the name of the user that you're recovering the deleted email for, click **Add**, and then click **OK**.</span></span>
    
8. <span data-ttu-id="3857d-159">Haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="3857d-159">Click **Next**.</span></span>
    
    <span data-ttu-id="3857d-160">Se muestra la página de **consulta de búsqueda** .</span><span class="sxs-lookup"><span data-stu-id="3857d-160">The **Search query** page is displayed.</span></span> <span data-ttu-id="3857d-161">Aquí es donde define los criterios de búsqueda que le ayudarán a encontrar los elementos que faltan en el buzón del usuario.</span><span class="sxs-lookup"><span data-stu-id="3857d-161">This is where you define the search criteria that will help you find the missing items in user's mailbox.</span></span> 
    
9. <span data-ttu-id="3857d-162">En la página **Consulta de búsqueda**, complete los campos siguientes:</span><span class="sxs-lookup"><span data-stu-id="3857d-162">On the **Search query** page, complete the following fields:</span></span> 
    
  - <span data-ttu-id="3857d-163">**Incluir todo el contenido** Seleccione esta opción para incluir todo el contenido en el buzón del usuario en los resultados de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="3857d-163">**Include all content** Select this option to include all content in the user's mailbox in the search results.</span></span> <span data-ttu-id="3857d-164">Si selecciona esta opción, no puede especificar más criterios de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="3857d-164">If you select this option, you can't specify additional search criteria.</span></span> 
    
  - <span data-ttu-id="3857d-165">**Filtrado basado en criterios** Seleccione esta opción para especificar los criterios de búsqueda, incluidas palabras clave, fechas de inicio y finalización, direcciones de remitente y destinatario, y tipos de mensaje.</span><span class="sxs-lookup"><span data-stu-id="3857d-165">**Filter based on criteria** Select this option to specify the search criteria, including keywords, start and end dates, sender and recipient addresses, and message types.</span></span> 
    
    ![Crear un quiera basado en criterios como palabras clave, intervalo de fechas, destinatarios y tipos de mensajes](media/ee47b833-9122-46a0-85e6-fcbe25be0dd5.png)
  
|<span data-ttu-id="3857d-167">**Field**</span><span class="sxs-lookup"><span data-stu-id="3857d-167">**Field**</span></span>|<span data-ttu-id="3857d-168">**Use esta para...**</span><span class="sxs-lookup"><span data-stu-id="3857d-168">**Use this to...**</span></span>|
|:-----|:-----|
|![Número uno en un círculo rosa](media/a4da261d-2516-48c5-b58a-9c452b9086b8.png)           <br/> |<span data-ttu-id="3857d-170">Especifique palabras clave, un intervalo de fechas, destinatarios y tipos de mensaje.</span><span class="sxs-lookup"><span data-stu-id="3857d-170">Specify keywords, date range, recipients, and message types.</span></span>  <br/> |
|![Número dos en un círculo rosa.](media/de3c1ab4-4f01-4026-b1ba-3265bdb32a89.png)           <br/> |<span data-ttu-id="3857d-172">Busque mensajes con palabras clave o frases y use operadores lógicos como **y** o **o**.</span><span class="sxs-lookup"><span data-stu-id="3857d-172">Search for messages with keywords or phrases, and use logical operators such as **AND** or **OR**.</span></span>  <br/> |
|![Número 3 en un círculo rosa.](media/60fa378c-6ac1-4cbd-a782-2fa7ca619dc6.png)           <br/> |<span data-ttu-id="3857d-174">Buscar mensajes enviados o recibidos en un intervalo de fechas.</span><span class="sxs-lookup"><span data-stu-id="3857d-174">Search for messages sent or received within a date range.</span></span>  <br/> |
|![Número 4 en un círculo rosa.](media/1a0ff2ce-0942-405a-94e3-9bfeb1e5059e.png)           <br/> |<span data-ttu-id="3857d-176">Buscar mensajes recibidos o enviados a personas específicas.</span><span class="sxs-lookup"><span data-stu-id="3857d-176">Search for messages received from or sent to specific people.</span></span>  <br/> |
|![Número cinco en un círculo rosa.](media/878cc815-0165-49ba-a1ee-9236e5980403.png)           <br/> |<span data-ttu-id="3857d-178">Busque todos los tipos de mensajes o seleccione unos específicos.</span><span class="sxs-lookup"><span data-stu-id="3857d-178">Search for all message types or select specific ones.</span></span>  <br/> |
   
    > [!TIP]
    >  Here's a few tips about how to build a search query to find missing items. Try to get as much information from the user to help you create a search query so you can find what you're looking for. >  If you not sure how to find a missing message, consider using the **Include all content** option. The search results will include all items in the user's Recoverable Items folder, including the hidden folder (called the Purges folder) that contain items that have been purged by the user. Then you can go to Step 3, copy the results to a discovery mailbox, and look at the message in the hidden folder. >  If you know approximately when the missing message was originally sent or received by the user, use the **Specify start date** and **Specify end date** options to provide a date range. This will return all messages sent or received by the user within that date range. Specifying a date range is a really good way to narrow the search results. >  If you know who sent the missing email, use the **From** box to specify this sender. >  If you want to narrow the search results to different types of mailbox items, click **Select message types**, click **Select the message types to search**, and then choose a specific message type to search for. For example, you can search only for calendar items or contacts. Here's a screenshot of the different message types you can search for; the default is to search for all message types. 
  
    Click **Next** when you've completed the **Search query** page. 
    
10. <span data-ttu-id="3857d-179">En la página **configuración de conservación local** , haga clic en **Finalizar** para iniciar la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="3857d-179">On the **In-Place Hold settings** page, click **Finish** to start the search.</span></span> <span data-ttu-id="3857d-180">Para recuperar el correo electrónico eliminado, no hay razón para poner el buzón de correo del usuario en retención.</span><span class="sxs-lookup"><span data-stu-id="3857d-180">To recover deleted email, there's no reason to place the user's mailbox on hold.</span></span> 
    
    <span data-ttu-id="3857d-181">Una vez iniciada la búsqueda, Exchange mostrará una estimación del tamaño y la cantidad totales de elementos que devolverá la búsqueda en función de los criterios especificados.</span><span class="sxs-lookup"><span data-stu-id="3857d-181">After you start the search, Exchange will display an estimate of the total size and number of items that will be returned by the search based on the criteria you specified.</span></span>
    
11. <span data-ttu-id="3857d-182">Seleccione la búsqueda que acaba de crear y \*\*\*\*![haga clic](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) en actualizar actualización para actualizar la información que se muestra en el panel de detalles.</span><span class="sxs-lookup"><span data-stu-id="3857d-182">Select the search you just created and click **Refresh**![refresh](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) to update the information displayed in the details pane.</span></span> <span data-ttu-id="3857d-183">El estado de **Estimated Succeeded** indica que la búsqueda ha finalizado.</span><span class="sxs-lookup"><span data-stu-id="3857d-183">The status of **Estimate Succeeded** indicates that the search has finished.</span></span> <span data-ttu-id="3857d-184">Exchange también muestra una estimación del número total de elementos (y su tamaño) encontrados por la búsqueda en función de los criterios de búsqueda especificados en el paso 9.</span><span class="sxs-lookup"><span data-stu-id="3857d-184">Exchange also displays an estimate of the total number of items (and their size) found by the search based on the search criteria you specified in step 9.</span></span> 
    
12. <span data-ttu-id="3857d-185">En el panel de detalles, haga clic en **vista previa de resultados** de la búsqueda para ver los elementos que se encontraron.</span><span class="sxs-lookup"><span data-stu-id="3857d-185">In the details pane, click **Preview search results** to view the items that were found.</span></span> <span data-ttu-id="3857d-186">Esto puede ayudarle a identificar los elementos que está buscando.</span><span class="sxs-lookup"><span data-stu-id="3857d-186">This might help you identify the item(s) that you're looking for.</span></span> <span data-ttu-id="3857d-187">Si encuentra los elementos que está intentando recuperar, vaya al paso 4 para exportar los resultados de la búsqueda a un archivo PST.</span><span class="sxs-lookup"><span data-stu-id="3857d-187">If you find the item(s) you're trying to recover, go to step 4 to export the search results to a PST file.</span></span> 
    
    ![Haga clic en vista previa de resultados de búsqueda para ver el elemento que está intentando recuperar](media/a2cea921-dafa-45d6-97d4-ae45a226b8d3.png)
  
13. <span data-ttu-id="3857d-189">Si no encuentra lo que está buscando, puede revisar los criterios de búsqueda seleccionando la búsqueda, haciendo clic en **Editar**![icono](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif)editar y, a continuación, haciendo clic en **consulta de búsqueda**.</span><span class="sxs-lookup"><span data-stu-id="3857d-189">If you don't find what you're looking for, you can revise your search criteria by selecting the search, clicking **Edit**![Edit icon](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif), and then clicking **Search query**.</span></span> <span data-ttu-id="3857d-190">Cambie los criterios de búsqueda y vuelva a ejecutar la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="3857d-190">Change the search criteria and then rerun the search.</span></span>
    
[<span data-ttu-id="3857d-191">Return to top</span><span class="sxs-lookup"><span data-stu-id="3857d-191">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="optional-step-3-copy-the-search-results-to-a-discovery-mailbox"></a><span data-ttu-id="3857d-192">Opcional Paso 3: copiar los resultados de la búsqueda en un buzón de correo de detección</span><span class="sxs-lookup"><span data-stu-id="3857d-192">(Optional) Step 3: Copy the search results to a discovery mailbox</span></span>
<span data-ttu-id="3857d-193"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="3857d-193"></span></span>

<span data-ttu-id="3857d-194">Si no puede encontrar un elemento al obtener una vista previa de los resultados de la búsqueda o si desea ver qué elementos se encuentran en la carpeta elementos recuperables del usuario, puede copiar los resultados de la búsqueda en un buzón especial (denominado buzón de correo de detección) y, a continuación, abrir el buzón en Outlook en la web t o ver los elementos reales.</span><span class="sxs-lookup"><span data-stu-id="3857d-194">If you can't find an items by previewing the search results or if you want to see which items are in the user's Recoverable Items folder, then you can copy the search results to a special mailbox (called a discovery mailbox) and then open that mailbox in Outlook on the web to view the actual items.</span></span> <span data-ttu-id="3857d-195">La mejor razón para copiar los resultados de la búsqueda es que pueda ver los elementos de la carpeta elementos recuperables del usuario.</span><span class="sxs-lookup"><span data-stu-id="3857d-195">The best reason to copy the search results is so you can view the items in the user's Recoverable Items folder.</span></span> <span data-ttu-id="3857d-196">Es muy probable que el elemento que está intentando recuperar se encuentre en la subcarpeta depuraciones.</span><span class="sxs-lookup"><span data-stu-id="3857d-196">More than likely, the item you're trying to recover is located in the Purges subfolder.</span></span> 
  
1. <span data-ttu-id="3857d-197">En el centro de administración de Exchange, vaya a **conservación de exhibición &amp; de documentos electrónicos local de** **Administración** \> de cumplimiento.</span><span class="sxs-lookup"><span data-stu-id="3857d-197">In the Exchange admin center, go to **Compliance management** \> **In-Place eDiscovery &amp; Hold**.</span></span>
    
2. <span data-ttu-id="3857d-198">En la lista de búsquedas, seleccione la búsqueda que ha creado en el paso 2.</span><span class="sxs-lookup"><span data-stu-id="3857d-198">In the list of searches, select the search that you created in Step 2.</span></span>
    
3. <span data-ttu-id="3857d-199">Haga clic en buscar búsqueda y, a continuación, haga clic en **copiar resultados de búsqueda** en la lista desplegable. \*\*\*\*![](media/c94e8591-7044-4650-a0d1-c57c0633ab4f.png)</span><span class="sxs-lookup"><span data-stu-id="3857d-199">Click **Search**![search](media/c94e8591-7044-4650-a0d1-c57c0633ab4f.png), and then click **Copy search results** from the drop-down list.</span></span> 
    
    ![Haga clic en buscar y, a continuación, en copiar resultados de búsqueda](media/7888df82-94b4-4e44-8a53-f66854dc7c86.png)
  
4. <span data-ttu-id="3857d-201">En la página **copiar resultados de búsqueda** , haga clic en **examinar**.</span><span class="sxs-lookup"><span data-stu-id="3857d-201">On the **Copy Search Results** page, click **Browse**.</span></span>
    
    ![Deje las casillas desactivadas al recuperar los elementos eliminados](media/37f27999-a5b2-4fed-87e2-bad6dc23cdae.png)
  
5. <span data-ttu-id="3857d-203">En **nombre para mostrar**, haga clic en **buzón de búsqueda de detección**y, a continuación, en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="3857d-203">Under **Display Name**, click **Discovery Search Mailbox**, and then click **OK**.</span></span>
    
    ![Copiar los resultados de la búsqueda en el buzón de búsqueda de detección predeterminado](media/36e8ef47-0035-4982-9ed6-426719c5f9ec.png)
  
    > [!NOTE]
    > <span data-ttu-id="3857d-205">El buzón de búsqueda de detección es un buzón de correo de detección predeterminado que se crea automáticamente en su organización de Office 365.</span><span class="sxs-lookup"><span data-stu-id="3857d-205">The Discovery Search Mailbox is a default discovery mailbox that is automatically created in your Office 365 organization.</span></span> 
  
6. <span data-ttu-id="3857d-206">De nuevo en la página **copiar resultados de búsqueda** , haga clic en **copiar** para iniciar el proceso de copia de los resultados de la búsqueda en el buzón de búsqueda de detección.</span><span class="sxs-lookup"><span data-stu-id="3857d-206">Back on the **Copy Search Results** page, click **Copy** to start the process to copy the search results to the Discovery Search Mailbox.</span></span> 
    
    ![Haga clic en copiar para copiar los resultados de la búsqueda en el buzón de búsqueda de detección](media/71307a9d-f7a1-4e01-ae37-1d49040cc3fd.png)
  
7. <span data-ttu-id="3857d-208">Haga \*\*\*\*![clic en](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) actualizar actualización para actualizar la información sobre el estado de copia que se muestra en el panel de detalles.</span><span class="sxs-lookup"><span data-stu-id="3857d-208">Click **Refresh**![refresh](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) to update the information about the copying status that is displayed in the details pane.</span></span> 
    
8. <span data-ttu-id="3857d-209">Una vez completada la copia, haga clic en **abrir** para abrir el buzón de búsqueda de detección para ver los resultados de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="3857d-209">When the copying is complete, click **Open** to open the Discovery Search Mailbox to view the search results.</span></span> 
    
    ![Haga clic en abrir para ir al buzón de búsqueda de detección para ver los resultados de la búsqueda](media/6cc81e0f-ceed-4464-9040-79b6f920de35.png)
  
    <span data-ttu-id="3857d-211">Los resultados de la búsqueda que se copian en el buzón de búsqueda de detección se colocan en una carpeta que tiene el mismo nombre que la búsqueda de exhibición de documentos electrónicos local.</span><span class="sxs-lookup"><span data-stu-id="3857d-211">The search results copied to the Discovery Search Mailbox are placed in a folder that has the same name as the In-Place eDiscovery search.</span></span> <span data-ttu-id="3857d-212">Puede hacer clic en una carpeta para mostrar los elementos de esa carpeta.</span><span class="sxs-lookup"><span data-stu-id="3857d-212">You can click a folder to display the items in that folder.</span></span>
    
    ![Resultados de búsqueda en el buzón de búsqueda de detección; los elementos de la carpeta purgas solo los puede recuperar un administrador](media/2ef8e5fb-3e63-4f62-938e-307efe9f6998.gif)
  
    <span data-ttu-id="3857d-214">Cuando se ejecuta una búsqueda, también se busca en la carpeta elementos recuperables del usuario.</span><span class="sxs-lookup"><span data-stu-id="3857d-214">When you run a search, the user's Recoverable Items folder is also searched.</span></span> <span data-ttu-id="3857d-215">Esto significa que si los elementos de la carpeta elementos recuperables cumplen los criterios de búsqueda, se incluirán en los resultados de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="3857d-215">That means if items in the Recoverable Items folder meet the search criteria, they are included in the search results.</span></span> <span data-ttu-id="3857d-216">Los elementos de la carpeta eliminaciones son elementos eliminados permanentemente por el usuario (eliminando un elemento de la carpeta elementos eliminados o seleccionándolo y presionando **Mayús + Supr**.</span><span class="sxs-lookup"><span data-stu-id="3857d-216">Items in the Deletions folder are items that the user permanently deleted (by deleting an item from the Deleted Items folder or by selecting it and pressing **Shift+Delete**.</span></span> <span data-ttu-id="3857d-217">Un usuario puede usar la herramienta recuperar elementos eliminados de Outlook o Outlook en la web para recuperar elementos de la carpeta eliminaciones.</span><span class="sxs-lookup"><span data-stu-id="3857d-217">A user can use the Recover Deleted Items tool in Outlook or Outlook on the web to recover items in the Deletions folder.</span></span> <span data-ttu-id="3857d-218">Los elementos de la carpeta purgas son elementos que el usuario ha purgado mediante la herramienta recuperar elementos eliminados o elementos que una directiva ha aplicado automáticamente al buzón.</span><span class="sxs-lookup"><span data-stu-id="3857d-218">Items in the Purges folder are items that the user purged by using the Recover Deleted Items tool or items they were automatically purged by a policy applied to the mailbox.</span></span> <span data-ttu-id="3857d-219">En cualquier caso, solo un administrador puede recuperar elementos de la carpeta depuraciones.</span><span class="sxs-lookup"><span data-stu-id="3857d-219">In either case, only an admin can recover items in the Purges folder.</span></span> 
    
    > [!TIP]
    > <span data-ttu-id="3857d-220">Si un usuario no encuentra un elemento eliminado mediante la herramienta elementos recuperables, pero ese elemento todavía se puede recuperar (lo que significa que no se ha quitado de forma permanente del buzón de correo), es más probable que se encuentre en la carpeta depuraciones.</span><span class="sxs-lookup"><span data-stu-id="3857d-220">If a user can't find a deleted item using the Recoverable Items tool, but that item is still recoverable (meaning that it hasn't been permanently removed from the mailbox), it's more than likely located in the Purges folder.</span></span> <span data-ttu-id="3857d-221">Por lo tanto, asegúrese de buscar en la carpeta purgas el elemento eliminado que está intentando recuperar para un usuario.</span><span class="sxs-lookup"><span data-stu-id="3857d-221">So, be sure to look in the Purges folder for the deleted item you're trying to recover for a user.</span></span> 
  
[<span data-ttu-id="3857d-222">Return to top</span><span class="sxs-lookup"><span data-stu-id="3857d-222">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-4-export-the-search-results-to-a-pst-file"></a><span data-ttu-id="3857d-223">Paso 4: exportar los resultados de la búsqueda a un archivo PST</span><span class="sxs-lookup"><span data-stu-id="3857d-223">Step 4: Export the search results to a PST file</span></span>
<span data-ttu-id="3857d-224"><a name="step4"> </a></span><span class="sxs-lookup"><span data-stu-id="3857d-224"></span></span>

<span data-ttu-id="3857d-225">Una vez que encuentre el elemento que está intentando recuperar para un usuario, el siguiente paso consiste en exportar los resultados de la búsqueda que ejecutó en el paso 2 a un archivo PST.</span><span class="sxs-lookup"><span data-stu-id="3857d-225">After you find the item you're trying to recover for a user, the next step is to export the results from the search you ran in Step 2 to a PST file.</span></span> <span data-ttu-id="3857d-226">El usuario usará este archivo PST en el siguiente paso para restaurar el elemento eliminado en su buzón de correo.</span><span class="sxs-lookup"><span data-stu-id="3857d-226">The user will use this PST file in the next step to restore the deleted item to their mailbox.</span></span>
  
1. <span data-ttu-id="3857d-227">En el centro de administración de Exchange, vaya a **conservación de exhibición &amp; de documentos electrónicos local de** **Administración** \> de cumplimiento.</span><span class="sxs-lookup"><span data-stu-id="3857d-227">In the Exchange admin center, go to **Compliance management** \> **In-Place eDiscovery &amp; Hold**.</span></span>
    
2. <span data-ttu-id="3857d-228">En la lista de búsquedas, seleccione la búsqueda que ha creado en el paso 2.</span><span class="sxs-lookup"><span data-stu-id="3857d-228">In the list of searches, select the search that you created in Step 2.</span></span>
    
3. <span data-ttu-id="3857d-229">Haga clic en **exportar a un archivo pst**.</span><span class="sxs-lookup"><span data-stu-id="3857d-229">Click **Export to a PST file**.</span></span>
    
    ![Haga clic en exportar a un archivo PST](media/4e59ae17-4541-43f4-a6d1-1f8b9ba9404b.png)
  
4. <span data-ttu-id="3857d-231">Si se le pide que instale la herramienta de exportación de exhibición de documentos electrónicos, haga clic en **Ejecutar**.</span><span class="sxs-lookup"><span data-stu-id="3857d-231">If you're prompted to install the eDiscovery Export Tool, click **Run**.</span></span>
    
5. <span data-ttu-id="3857d-232">En la herramienta de exportación de PST de eDiscovery, haga clic en **examinar** para especificar la ubicación en la que desea descargar el archivo pst.</span><span class="sxs-lookup"><span data-stu-id="3857d-232">In the eDiscovery PST Export Tool, click **Browse** to specify the location where you want to download the PST file.</span></span> 
    
    ![La herramienta de exportación de PST de eDiscovery](media/17274d27-992e-4034-8133-8f793f554e6c.png)
  
    <span data-ttu-id="3857d-234">Puede omitir las opciones para habilitar la desduplicación e incluir elementos no aptos para la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="3857d-234">You can ignore the options to enable deduplication and include unsearchable items.</span></span>
    
6. <span data-ttu-id="3857d-235">Haga clic en **iniciar** para descargar el archivo pst en su equipo.</span><span class="sxs-lookup"><span data-stu-id="3857d-235">Click **Start** to download the PST file to your computer.</span></span> 
    
    <span data-ttu-id="3857d-236">La **herramienta de exportación de PST de eDiscovery** muestra información de estado sobre el proceso de exportación.</span><span class="sxs-lookup"><span data-stu-id="3857d-236">The **eDiscovery PST Export Tool** displays status information about the export process.</span></span> <span data-ttu-id="3857d-237">Una vez completada la exportación, puede tener acceso al archivo en la ubicación donde se ha descargado.</span><span class="sxs-lookup"><span data-stu-id="3857d-237">When the export is complete, you can access the file in the location where it was downloaded.</span></span> 
    
[<span data-ttu-id="3857d-238">Return to top</span><span class="sxs-lookup"><span data-stu-id="3857d-238">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-5-restore-the-recovered-items-to-the-users-mailbox"></a><span data-ttu-id="3857d-239">Paso 5: restaurar los elementos recuperados en el buzón de correo del usuario</span><span class="sxs-lookup"><span data-stu-id="3857d-239">Step 5: Restore the recovered items to the user's mailbox</span></span>
<span data-ttu-id="3857d-240"><a name="step5"> </a></span><span class="sxs-lookup"><span data-stu-id="3857d-240"></span></span>

<span data-ttu-id="3857d-241">El último paso consiste en usar el archivo PST que se exportó en el paso 4 para restaurar los elementos recuperados en el buzón de correo del usuario.</span><span class="sxs-lookup"><span data-stu-id="3857d-241">The final step is to use the PST file that was exported in step 4 to restore the recovered items to the user's mailbox.</span></span> <span data-ttu-id="3857d-242">Después de enviar el archivo PST al usuario, el resto de este paso es realizado por el usuario para abrir el archivo PST y mover los elementos recuperados a otra carpeta en su buzón.</span><span class="sxs-lookup"><span data-stu-id="3857d-242">After you send the PST file to the user, the remainder of this step is performed by the user to open the PST file and then move the recovered items to another folder in their mailbox.</span></span> <span data-ttu-id="3857d-243">Para obtener instrucciones paso a paso, también puede enviar al usuario un vínculo a este tema: [abrir y cerrar archivos de datos de Outlook (. pst)](https://support.office.com/article/381b776d-7511-45a0-953a-0935c79d24f2).</span><span class="sxs-lookup"><span data-stu-id="3857d-243">For step-by-step instructions, you can also send the user a link to this topic: [Open and close Outlook Data Files (.pst)](https://support.office.com/article/381b776d-7511-45a0-953a-0935c79d24f2).</span></span> <span data-ttu-id="3857d-244">O bien, puede enviar un vínculo al usuario a la siguiente sección [Restaurar elementos eliminados a un buzón de correo mediante un archivo pst](recover-deleted-items-in-a-mailbox.md#restoredeleteditems) a continuación y pedirle que realice estos pasos.</span><span class="sxs-lookup"><span data-stu-id="3857d-244">Or you can send the user a link to the [Restore deleted items to a mailbox using a PST file](recover-deleted-items-in-a-mailbox.md#restoredeleteditems) section below and ask them to perform these steps.</span></span> 
  
 <span data-ttu-id="3857d-245">**Enviar el archivo PST al usuario**</span><span class="sxs-lookup"><span data-stu-id="3857d-245">**Send the PST file to the user**</span></span>
  
<span data-ttu-id="3857d-246">El último paso que debe realizar es enviar al usuario el archivo PST que se exportó en el paso 4.</span><span class="sxs-lookup"><span data-stu-id="3857d-246">The final step that you need to perform is sending the PST file that was exported in step 4 to the user.</span></span> <span data-ttu-id="3857d-247">Hay varias formas de hacerlo:</span><span class="sxs-lookup"><span data-stu-id="3857d-247">There are a few ways to do this:</span></span>
  
- <span data-ttu-id="3857d-248">Adjunte el archivo PST a un mensaje de correo electrónico.</span><span class="sxs-lookup"><span data-stu-id="3857d-248">Attach the PST file to an email message.</span></span> <span data-ttu-id="3857d-249">Si Outlook está configurado para bloquear los archivos PST, tendrá que comprimir el archivo y, a continuación, adjuntarlo al mensaje.</span><span class="sxs-lookup"><span data-stu-id="3857d-249">If Outlook is configured to block PST files, then you will have to zip the file and then attach it to the message.</span></span> <span data-ttu-id="3857d-250">A continuación se describe cómo:</span><span class="sxs-lookup"><span data-stu-id="3857d-250">Here's how:</span></span>
    
1. <span data-ttu-id="3857d-251">En el explorador de Windows o en el explorador de archivos, vaya al archivo PST.</span><span class="sxs-lookup"><span data-stu-id="3857d-251">In Windows Explorer or File Explorer, browse to the PST file.</span></span>
    
2. <span data-ttu-id="3857d-252">Haga clic con el botón derecho en el archivo y, después, seleccione **Enviar a** \> **carpeta comprimida (en zip)**.</span><span class="sxs-lookup"><span data-stu-id="3857d-252">Right-click the file, and then select **Send to** \> **Compressed (zipped) folder**.</span></span> <span data-ttu-id="3857d-253">Windows crea un nuevo archivo zip y le asigna el mismo nombre que el archivo PST.</span><span class="sxs-lookup"><span data-stu-id="3857d-253">Windows creates a new zip file and gives it an identical name as the PST file.</span></span>
    
3. <span data-ttu-id="3857d-254">Adjunte el archivo PST comprimido a un mensaje de correo electrónico y envíelo al usuario, quien podrá descomprimir el archivo simplemente haciendo clic en él.</span><span class="sxs-lookup"><span data-stu-id="3857d-254">Attach the compressed PST file to an email message and send it to the user, who can then decompress the file just by clicking it.</span></span>
    
- <span data-ttu-id="3857d-255">Copie el archivo PST en una carpeta compartida al que el usuario pueda tener acceso y recuperarlo.</span><span class="sxs-lookup"><span data-stu-id="3857d-255">Copy the PST file to a shared folder that the user can access and retrieve it.</span></span>
    
<span data-ttu-id="3857d-256">Los pasos de la siguiente sección son realizados por el usuario para restaurar los elementos eliminados en su buzón de correo.</span><span class="sxs-lookup"><span data-stu-id="3857d-256">The steps in the next section are performed by the user to restore the deleted items to their mailbox.</span></span>
  
 <a name="restoredeleteditems"></a>
<span data-ttu-id="3857d-257">**Restaurar elementos eliminados en un buzón con un archivo PST**</span><span class="sxs-lookup"><span data-stu-id="3857d-257">**Restore deleted items to a mailbox using a PST file**</span></span>
  
<span data-ttu-id="3857d-258">Tiene que usar la aplicación de escritorio de Outlook para restaurar un elemento eliminado mediante un archivo PST.</span><span class="sxs-lookup"><span data-stu-id="3857d-258">You have to use the Outlook desktop app to restore a deleted item by using a PST file.</span></span> <span data-ttu-id="3857d-259">No puede usar Outlook Web App u Outlook en la web para abrir un archivo PST.</span><span class="sxs-lookup"><span data-stu-id="3857d-259">You can't use Outlook Web App or Outlook on the web to open a PST file.</span></span>
  
1. <span data-ttu-id="3857d-260">En Outlook 2013 o en Outlook 2016, haga clic en la pestaña **archivo** .</span><span class="sxs-lookup"><span data-stu-id="3857d-260">In Outlook 2013 or Outlook 2016, click the **File** tab.</span></span> 
    
2. <span data-ttu-id="3857d-261">Haga clic en \*\* &amp; abrir exportar\*\*y, a continuación, en **Abrir archivo de datos de Outlook**.</span><span class="sxs-lookup"><span data-stu-id="3857d-261">Click **Open &amp; Export**, and then click **Open Outlook Data File**.</span></span>
    
3. <span data-ttu-id="3857d-262">Vaya a la ubicación donde guardó el archivo PST que envió el administrador.</span><span class="sxs-lookup"><span data-stu-id="3857d-262">Browse to the location where you saved the PST file that your administrator sent.</span></span>
    
4. <span data-ttu-id="3857d-263">Seleccione el archivo PST y, a continuación, haga clic en **abrir**.</span><span class="sxs-lookup"><span data-stu-id="3857d-263">Select the PST and then click **Open**.</span></span>
    
    <span data-ttu-id="3857d-264">El archivo PST aparece en la barra de navegación izquierda en Outlook.</span><span class="sxs-lookup"><span data-stu-id="3857d-264">The PST file appears in the left-nav bar in Outlook.</span></span>
    
    ![El archivo PST aparece en la barra de navegación izquierda en Outlook](media/c9389392-d08a-4aa7-848c-4986d448b0f2.png)
  
5. <span data-ttu-id="3857d-266">Haga clic en las flechas para expandir el archivo PST y las carpetas que hay debajo para localizar el elemento que desea recuperar.</span><span class="sxs-lookup"><span data-stu-id="3857d-266">Click the arrows to expand the PST file and the folders under it to locate the item you want to recover.</span></span>
    
    ![Busque en la carpeta purgas el elemento que desee recuperar](media/d4e372d9-ac23-4e95-8639-d8da690fefa7.png)
  
    > [!TIP]
    > <span data-ttu-id="3857d-268">Busque en la carpeta purgas el elemento que desee recuperar.</span><span class="sxs-lookup"><span data-stu-id="3857d-268">Look in the Purges folder for the item you want to recover.</span></span> <span data-ttu-id="3857d-269">Se trata de una carpeta oculta a la que se mueven los elementos purgados.</span><span class="sxs-lookup"><span data-stu-id="3857d-269">This is a hidden folder that purged items are moved to.</span></span> <span data-ttu-id="3857d-270">Es probable que el elemento que el administrador haya recuperado esté en esta carpeta.</span><span class="sxs-lookup"><span data-stu-id="3857d-270">It's likely the item that your administrator recovered is in this folder.</span></span> 
  
6. <span data-ttu-id="3857d-271">Haga clic con el botón secundario en el elemento que desee recuperar y, a continuación, haga clic en **mover** \> **otra carpeta**.</span><span class="sxs-lookup"><span data-stu-id="3857d-271">Right-click the item you want to recover and then click **Move** \> **Other Folder**.</span></span>
    
    ![Haga clic en mover y, a continuación, seleccione otra carpeta](media/090063df-2aa0-444a-8e47-abd6fe6cf7a8.png)
  
7. <span data-ttu-id="3857d-273">Para mover el elemento a la bandeja de entrada, haga clic en **bandeja de entrada**y, a continuación, en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="3857d-273">To move the item to your inbox, click **Inbox**, and then click **OK**.</span></span>
    
    <span data-ttu-id="3857d-274">**Sugerencia:** Para recuperar otros tipos de elementos, realice una de las siguientes acciones:</span><span class="sxs-lookup"><span data-stu-id="3857d-274">**Tip:** To recover other types of items, do one of the following:</span></span> 
    
  - <span data-ttu-id="3857d-275">Para recuperar un elemento de calendario, haga clic con el botón secundario en él y, a continuación, haga clic en **mover** \> **calendario**de **otras carpetas** \> .</span><span class="sxs-lookup"><span data-stu-id="3857d-275">To recover a calendar item, right-click it, and then click **Move** \> **Other Folder** \> **Calendar**.</span></span>
    
  - <span data-ttu-id="3857d-276">Para recuperar un contacto, haga clic en él con el botón derecho y, a continuación, haga clic en **mover** \> **otros** \> **contactos**de carpeta.</span><span class="sxs-lookup"><span data-stu-id="3857d-276">To recover a contact, right-click it, and then click **Move** \> **Other Folder** \> **Contacts**.</span></span>
    
  - <span data-ttu-id="3857d-277">Para recuperar una tarea, haga clic con el botón secundario en ella y, a continuación, haga clic en **mover** \> **otras** \> **tareas**de carpeta.</span><span class="sxs-lookup"><span data-stu-id="3857d-277">To recover a task, right-click it, and then click **Move** \> **Other Folder** \> **Tasks**.</span></span>
    
![Seleccionar una carpeta para mover otros tipos de elementos](media/f8290131-43f2-46f1-bc07-228c2d83b96c.png)
  
    Note that calendar items, contacts, and tasks are located directly in the Purges folder, and not in a Calendar, Contacts, or Tasks subfolder. However, you can sort by **Type** to group similar types of items. 
    
8. <span data-ttu-id="3857d-279">Cuando haya terminado de recuperar los elementos eliminados, haga clic con el botón derecho en el archivo PST en la barra de navegación izquierda y seleccione **Cerrar "nombre de archivo pst"**.</span><span class="sxs-lookup"><span data-stu-id="3857d-279">When you're finished recovering deleted items, right-click the PST file in the left-nav bar and select **Close "name of PST file"**.</span></span>
    
[<span data-ttu-id="3857d-280">Return to top</span><span class="sxs-lookup"><span data-stu-id="3857d-280">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="more-information"></a><span data-ttu-id="3857d-281">Más información</span><span class="sxs-lookup"><span data-stu-id="3857d-281">More information</span></span>
<span data-ttu-id="3857d-282"><a name="moreinfo"> </a></span><span class="sxs-lookup"><span data-stu-id="3857d-282"></span></span>

- <span data-ttu-id="3857d-283">Es posible que un usuario pueda recuperar un elemento eliminado permanentemente si el período de retención de elementos eliminados para el elemento no ha expirado.</span><span class="sxs-lookup"><span data-stu-id="3857d-283">It might be possible for a user to recover a permanently deleted item if the deleted item retention period for the item hasn't expired.</span></span> <span data-ttu-id="3857d-284">Como administrador, es posible que haya especificado el tiempo que los elementos de la carpeta elementos recuperables estarán disponibles para la recuperación.</span><span class="sxs-lookup"><span data-stu-id="3857d-284">As an admin you may have specified how long items in the Recoverable Items folder are available for recovery.</span></span> <span data-ttu-id="3857d-285">Por ejemplo, puede haber una directiva que elimine todo lo que haya en la carpeta elementos eliminados de un usuario durante 30 días y otra directiva que permita a los usuarios recuperar los elementos de la carpeta elementos recuperables durante un máximo de 14 días.</span><span class="sxs-lookup"><span data-stu-id="3857d-285">For example, there might be a policy that deletes anything that's been in a user's Deleted Items folder for 30 days, and another policy that lets users recover items in the Recoverable Items folder for up to another 14 days.</span></span> <span data-ttu-id="3857d-286">Sin embargo, después de estos 14 días, es posible que pueda recuperar un elemento en el buzón de un usuario mediante los procedimientos de este tema.</span><span class="sxs-lookup"><span data-stu-id="3857d-286">However, after this 14 days, you may still be able to recover an item in a user's mailbox by using the procedures in this topic.</span></span>
    
- <span data-ttu-id="3857d-287">Los usuarios pueden recuperar un elemento eliminado si todavía no se ha purgado y si no ha expirado el período de retención de elementos eliminados para ese elemento.</span><span class="sxs-lookup"><span data-stu-id="3857d-287">Users can recover a deleted item if it hasn't been purged and if the deleted item retention period for that item hasn't expired.</span></span> <span data-ttu-id="3857d-288">Para ayudar a los usuarios a recuperar los elementos eliminados en su buzón de correo, señale a uno de los siguientes temas:</span><span class="sxs-lookup"><span data-stu-id="3857d-288">To help users recover deleted items in their mailbox, point them to one of the following topics:</span></span>
    
  - [<span data-ttu-id="3857d-289">Recuperación de elementos eliminados en Outlook para Windows</span><span class="sxs-lookup"><span data-stu-id="3857d-289">Recover deleted items in Outlook for Windows</span></span>](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
    
  - [<span data-ttu-id="3857d-290">Recuperar elementos eliminados en Outlook 2010</span><span class="sxs-lookup"><span data-stu-id="3857d-290">Recover deleted items in Outlook 2010</span></span>](https://support.office.com/article/cd9dfe12-8e8c-4a21-bbbf-4bd103a3f1fe)
    
  - [<span data-ttu-id="3857d-291">Recuperar elementos eliminados o correo electrónico en Outlook Web App</span><span class="sxs-lookup"><span data-stu-id="3857d-291">Recover deleted items or email in Outlook Web App</span></span>](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
    
  - [<span data-ttu-id="3857d-292">Restaurar mensajes de correo electrónico eliminados en Outlook en la web</span><span class="sxs-lookup"><span data-stu-id="3857d-292">Restore deleted email messages in Outlook on the web</span></span>](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
    
  - [<span data-ttu-id="3857d-293">Recuperar un contacto eliminado en Outlook</span><span class="sxs-lookup"><span data-stu-id="3857d-293">Recover a deleted contact in Outlook</span></span>](https://support.office.com/article/51c83288-6888-4dcd-8c99-4932daabf643)
    
  - [<span data-ttu-id="3857d-294">Restaurar mensajes de correo electrónico eliminados en Outlook.com</span><span class="sxs-lookup"><span data-stu-id="3857d-294">Restore deleted email messages in Outlook.com</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=623435)
    
[<span data-ttu-id="3857d-295">Volver al principio</span><span class="sxs-lookup"><span data-stu-id="3857d-295">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  

