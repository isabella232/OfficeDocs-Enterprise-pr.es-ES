---
title: Exhibición avanzada de documentos electrónicos para el entorno de desarrollo y pruebas de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: d4c49a6f-abfd-4d68-b353-259b4eefb033
description: 'Resumen: configure y demuestre la Exhibición avanzada de documentos electrónicos de Office 365 en el entorno de desarrollo y pruebas de Office 365.'
ms.openlocfilehash: c93900e07b8b9adbe0f1120eca77019b9dcc1eda
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897513"
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a><span data-ttu-id="bc7c9-103">Exhibición avanzada de documentos electrónicos para el entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="bc7c9-103">Advanced eDiscovery for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="bc7c9-104">**Resumen:** configure y demuestre la Exhibición avanzada de documentos electrónicos de Office 365 en el entorno de desarrollo y pruebas de Office 365.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-104">**Summary:** Configure and demonstrate Office 365 Advanced eDiscovery with sample data in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="bc7c9-p101">EDiscovery avanzada de Office 365 le permite buscar rápidamente y analizar información relevante a través de los datos que se almacenan en Office 365, incluido el correo electrónico y documentos. Esto puede ahorrar una gran cantidad de tiempo y gastos, especialmente en situaciones de litigio. Para obtener más información, vea [Office 365 avanzada exhibición de documentos electrónicos](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).</span><span class="sxs-lookup"><span data-stu-id="bc7c9-p101">Office 365 Advanced eDiscovery lets you quickly find and analyze relevant information across the data that is stored in Office 365, including email and documents. This can save enormous amounts of time and expense, especially in litigation situations. For more information, see [Office 365 Advanced eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).</span></span>
  
<span data-ttu-id="bc7c9-108">Con las instrucciones de este artículo, puede crear un pequeño conjunto de datos para una disputa contractual ficticia y analizarlo con la exhibición avanzada de documentos electrónicos.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-108">With the instructions in this article, you create a small set of data for a fictional contract dispute and analyze it with Advanced eDiscovery.</span></span>
  
> [!TIP]
> <span data-ttu-id="bc7c9-109">Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual de todos los artículos de la pila Guía de laboratorio de pruebas de One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-109">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a><span data-ttu-id="bc7c9-110">Fase 1: Crear el entorno de desarrollo y prueba de Office 365</span><span class="sxs-lookup"><span data-stu-id="bc7c9-110">Phase 1: Create your Office 365 dev/test environment</span></span>

<span data-ttu-id="bc7c9-111">Si desea probar avanzada exhibición de documentos electrónicos en una forma sencilla con los requisitos mínimos, siga las instrucciones que aparecen en la fase 2 y 3 de la fase del [entorno de desarrollo y prueba de Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="bc7c9-111">If you just want to test Advanced eDiscovery in a lightweight way with the minimum requirements, follow the instructions in Phase 2 and Phase 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="bc7c9-112">Si desea probar avanzada exhibición de documentos electrónicos en una empresa simulada, siga las instrucciones que aparecen en la [sincronización de directorios para el entorno de desarrollo y prueba de Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="bc7c9-112">If you want to test Advanced eDiscovery in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="bc7c9-p102">Prueba de exhibición de documentos electrónicos avanzada no requiere el entorno simulado enterprise, que incluye una intranet simulada conectada a Internet y sincronización de Active directory para un bosque de Windows Server AD. Se proporciona aquí como una opción para que pueda realizar las pruebas y la experimentación en un entorno que representa una organización típica.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-p102">Testing Advanced eDiscovery does not require the simulated enterprise environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can perform testing and experimentation in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a><span data-ttu-id="bc7c9-115">Fase 2: Crear datos de ejemplo para la exhibición avanzada de documentos electrónicos</span><span class="sxs-lookup"><span data-stu-id="bc7c9-115">Phase 2: Create example data for Advanced eDiscovery</span></span>

<span data-ttu-id="bc7c9-116">En este procedimiento, se crean mensajes de correo electrónico que posteriormente podrá analizar en un caso de exhibición avanzada de documentos electrónicos.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-116">In this procedure, you create email messages that will you later analyze in an Advanced eDiscovery case.</span></span>
  
1. <span data-ttu-id="bc7c9-117">Abra Internet Explorer e iniciar sesión en [https://outlook.com](https://outlook.com) a la cuenta de Outlook que creó en la fase 2 del[entorno de desarrollo y prueba de Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="bc7c9-117">Open Internet Explorer and sign in at [https://outlook.com](https://outlook.com) to the Outlook account you created in Phase 2 of[Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
    
  - <span data-ttu-id="bc7c9-118">Si usa el entorno de desarrollo y pruebas ligero, abra una sesión privada con Internet Explorer e inicie sesión desde el equipo local.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-118">If you are using the lightweight dev/test environment, open a private session of Internet Explorer and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="bc7c9-119">Si está utilizando el entorno de desarrollo o prueba enterprise simulado, use el portal de Azure ([https://portal.azure.com](https://portal.azure.com)) para conectarse a la máquina virtual CLIENT1 y, a continuación, iniciar sesión en desde CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-119">If you are using the simulated enterprise dev/test environment, use the Azure portal ([https://portal.azure.com](https://portal.azure.com)) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="bc7c9-120">En la pestaña **Correo de Outlook**, haga clic en **Nuevo**.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-120">On the **Outlook Mail** tab, click **New**.</span></span>
    
3. <span data-ttu-id="bc7c9-p103">En el cuadro **para**, escriba la dirección de correo electrónico de la cuenta de User6 de su suscripción de prueba ( **user6 @.** <organization name> **. onmicrosoft.com**).</span><span class="sxs-lookup"><span data-stu-id="bc7c9-p103">In **To**, type the email address of the User6 account of your trial subscription ( **user6@.**<organization name> **.onmicrosoft.com**).</span></span>
    
4. <span data-ttu-id="bc7c9-123">En el asunto, escriba **Correo electrónico de prueba 1**.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-123">For the subject, type **Test email 1**.</span></span>
    
5. <span data-ttu-id="bc7c9-124">En el cuerpo, escriba **Proyecto de contrato de Tailspin** y, a continuación, haga clic en **Enviar**.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-124">In the body, type **Tailspin contract draft**, and then click **Send**.</span></span>
    
6. <span data-ttu-id="bc7c9-125">En la pestaña **Correo de Outlook**, haga clic en **Nuevo**.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-125">On the **Outlook Mail** tab, click **New**.</span></span>
    
7. <span data-ttu-id="bc7c9-126">En **Para**, escriba la dirección de correo electrónico de la cuenta de User6 de su suscripción de prueba.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-126">In **To**, type the email address of the User6 account of your trial subscription.</span></span>
    
8. <span data-ttu-id="bc7c9-127">En el asunto, escriba **Correo electrónico de prueba 2**.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-127">For the subject, type **Test email 2**.</span></span>
    
9. <span data-ttu-id="bc7c9-128">En el cuerpo, escriba **Almuerzo de negocios de Tailspin** y, a continuación, haga clic en **Enviar**.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-128">In the body, type **Tailspin lunch meeting**, and then click **Send**.</span></span>
    
10. <span data-ttu-id="bc7c9-129">En la pestaña **Correo de Outlook**, haga clic en **Nuevo**.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-129">On the **Outlook Mail** tab, click **New**.</span></span>
    
11. <span data-ttu-id="bc7c9-130">En **Para**, escriba la dirección de correo electrónico de la cuenta de User6 de su suscripción de prueba.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-130">In **To**, type the email address of the User6 account of your trial subscription.</span></span>
    
12. <span data-ttu-id="bc7c9-131">En el asunto, escriba **Correo electrónico de prueba 3**.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-131">For the subject, type **Test email 3**.</span></span>
    
13. <span data-ttu-id="bc7c9-132">En el cuerpo, escriba **Desacuerdo con el contrato de Tailspin** y, después, haga clic en **Enviar**.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-132">In the body, type **Tailspin contract disagreement**, and then click **Send**.</span></span>
    
14. <span data-ttu-id="bc7c9-133">Haga clic en el icono de usuario en la esquina superior derecha y, a continuación, haga clic en **Cerrar sesión**.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-133">Click the user icon in the upper right corner, and then click **Sign out**.</span></span>
    
15. <span data-ttu-id="bc7c9-134">Abrir una nueva pestaña e inicie sesión en el portal de Office 365 ([https://portal.office.com](https://portal.office.com)) con el nombre de cuenta y la contraseña de la cuenta de User6 de su suscripción de prueba.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-134">Open a new tab and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) with the account name and password of the User6 account of your trial subscription.</span></span>
    
16. <span data-ttu-id="bc7c9-135">En la pestaña **Portal de Office 365**, haga clic en **Correo**.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-135">On the **Office 365 portal** tab, click **Mail**.</span></span>
    
17. <span data-ttu-id="bc7c9-136">En la ficha **correo - User6 - Outlook** , compruebe que User6 ha recibido todos los tres correos electrónicos de la cuenta de correo electrónico de Outlook.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-136">On the **Mail - User6 - Outlook** tab, check that User6 received all three emails from the Outlook email account.</span></span>
    
18. <span data-ttu-id="bc7c9-137">Vuelva a la pestaña **Portal de Office 365** de User6.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-137">Switch back to the **Office 365 portal tab** for User6.</span></span>
    
19. <span data-ttu-id="bc7c9-138">Haga clic en el icono de usuario en la esquina superior derecha y después en **Cerrar sesión**.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-138">Click the user icon in the upper right corner, and then click **Sign out.**</span></span>
    
<span data-ttu-id="bc7c9-139">En este procedimiento, se crean dos documentos de Word que posteriormente podrá analizar en un caso de exhibición avanzada de documentos electrónicos.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-139">In this procedure, you create two Word documents that will you will later analyze in an Advanced eDiscovery case.</span></span>
  
1. <span data-ttu-id="bc7c9-140">En la página **Office**, haga clic en **Iniciar sesión**, inicie sesión con las credenciales de su cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-140">On the **Office** page, click **Sign in,** sign in with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="bc7c9-141">En una nueva pestaña, obtener acceso a la dirección URL del sitio de SharePoint de producción: **https://** <fictional organization name> **.sharepoint.com/sites/production**</span><span class="sxs-lookup"><span data-stu-id="bc7c9-141">On a new tab, access the URL of your Production SharePoint site: **https://**<fictional organization name> **.sharepoint.com/sites/production**</span></span>
    
3. <span data-ttu-id="bc7c9-142">En la pestaña **Colección de sitios de producción**, en **Documentos**, haga clic en **Nuevo > Documento de Word**.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-142">On the **Production site collection** tab, under **Documents**, click **New > Word Document**.</span></span>
    
4. <span data-ttu-id="bc7c9-143">En la página de **Word Online**, escriba **Proyecto de contrato de Tailspin**, espere hasta que se muestre **Guardado** en el título y, después, cierre la pestaña de la página de **Word Online**.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-143">On the **Word Online** page, type **Tailspin draft contract**, wait until it displays **Saved** in the title, and then close the **Word Online** page tab.</span></span>
    
5. <span data-ttu-id="bc7c9-144">En la pestaña **Colección de sitios de producción**, en **Documentos**, haga clic en **Nuevo > Documento de Word**.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-144">On the **Production site collection** tab, under **Documents**, click **New > Word Document**.</span></span>
    
6. <span data-ttu-id="bc7c9-145">	En la pestaña de *\*Word Online*\*, escriba *\*Notas del conflicto del contrato de Tailspin*\*, espere hasta que se muestre *\*Guardado** en el título y, después, cierre la pestaña *\*Word Online*\*.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-145">On the **Word Online** tab, type **Tailspin contract dispute notes**, wait until it displays **Saved** in the title, and then close the **Word Online** tab.</span></span>
    
7. <span data-ttu-id="bc7c9-146">En la pestaña **Colección de sitios de producción**, debería ver **Documento** y **Documento1** en la lista de documentos.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-146">On the **Production site collection** tab, you should see **Document** and **Document1** in the list of documents.</span></span>
    
8. <span data-ttu-id="bc7c9-147">Cierre la pestaña **Colección de sitios de producción**.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-147">Close the **Production site collection** tab.</span></span>
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a><span data-ttu-id="bc7c9-148">Fase 3: Uso avanzado exhibición de documentos electrónicos para un litigio legal</span><span class="sxs-lookup"><span data-stu-id="bc7c9-148">Phase 3: Use Advanced eDiscovery for a legal dispute</span></span>

<span data-ttu-id="bc7c9-p104">Desafortunadamente, un conflicto contractual entre su organización y Tailspin Toys ha alcanzado el punto de acción legal. En este procedimiento, crear y configurar un caso de exhibición de documentos electrónicos avanzadas para buscar y analizar correo electrónico y documentos que contienen el texto "Contrato Tailspin".</span><span class="sxs-lookup"><span data-stu-id="bc7c9-p104">Unfortunately, a contract dispute between your organization and Tailspin Toys has reached the point of legal action. In this procedure, you create and configure an Advanced eDiscovery case to search for and analyze email and documents that contain the text "Tailspin contract".</span></span>
  
<span data-ttu-id="bc7c9-151">El proceso para utilizar la exhibición avanzada de documentos electrónicos es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="bc7c9-151">The process for using Advanced eDiscovery is the following:</span></span>
  
- <span data-ttu-id="bc7c9-152">Crear una búsqueda en la seguridad &amp; centro de cumplimiento, analizar sus resultados y, a continuación, preparar los resultados de la exhibición de documentos electrónicos avanzadas.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-152">Create a search in the Security &amp; Compliance center, analyze its results, and then prepare the results for Advanced eDiscovery.</span></span>
    
- <span data-ttu-id="bc7c9-153">Cree y configure un caso en la exhibición avanzada de documentos electrónicos y analice los resultados de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-153">Create and configure a case in Advanced eDiscovery and analyze the search results.</span></span>
    
<span data-ttu-id="bc7c9-154">En este procedimiento, se crea una búsqueda en la seguridad &amp; cumplimiento del Centro para "Contrato Tailspin", busque en los resultados y, a continuación, preparar los resultados de la exhibición de documentos electrónicos avanzadas.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-154">In this procedure, you create a search in the Security &amp; Compliance center for "Tailspin contract", look at the results, and then prepare the results for Advanced eDiscovery.</span></span>
  
1. <span data-ttu-id="bc7c9-155">En la pestaña **Portal de Office 365**, haga clic en **Administrador**.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-155">From the **Office 365 portal** tab, click **Admin**.</span></span>
    
2. <span data-ttu-id="bc7c9-156">En el panel de navegación izquierdo de la pestaña Centro de administración, haga clic en **Centros de administración > Cumplimiento**.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-156">In the left navigation of the Admin center tab, click **Admin centers > Compliance**.</span></span>
    
3. <span data-ttu-id="bc7c9-157">En la **seguridad &amp; cumplimiento** ficha, haga clic en **permisos**.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-157">On the **Security &amp; Compliance** tab, click **Permissions**.</span></span>
    
4. <span data-ttu-id="bc7c9-158">En la lista **Permisos**, haga doble clic en **Administración de organización**.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-158">In the **Permissions** list, double-click **Organization Management**.</span></span>
    
5. <span data-ttu-id="bc7c9-159">En la ventana **Grupo de roles**, en **Miembros**, haga clic en el signo más.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-159">In the **Role Group** window, under **Members**, click the plus sign.</span></span>
    
6. <span data-ttu-id="bc7c9-160">En la ventana **Seleccionar miembros**, haga doble clic en el nombre de la cuenta de administrador y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-160">In the **Select Members** window, double-click the name of your administrator account, and then click **OK**.</span></span>
    
7. <span data-ttu-id="bc7c9-161">En la ventana \*\*Grupo de roles \*\*, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-161">In the **Role Group** window, click **Save**.</span></span>
    
8. <span data-ttu-id="bc7c9-162">En la lista **Permisos**, haga doble clic en \*\*Administrador de exhibición de documentos electrónicos \*\*.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-162">In the **Permissions** list, double-click **eDiscovery Manager**.</span></span>
    
9. <span data-ttu-id="bc7c9-163">En la ventana **Grupo de roles**, en \*\*Administrador de exhibición de documentos electrónicos \*\*, haga clic en el icono de signo más.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-163">In the **Role Group** window, under **eDiscovery Administrator**, click the plus icon.</span></span>
    
10. <span data-ttu-id="bc7c9-164">En la ventana **Seleccionar miembros**, haga doble clic en el nombre de la cuenta de administrador y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-164">In the **Select Members** window, double-click the name of your administrator account, and then click **OK**.</span></span>
    
11. <span data-ttu-id="bc7c9-165">En la ventana \*\*Grupo de roles \*\*, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-165">In the **Role Group** window, click **Save**.</span></span>
    
12. <span data-ttu-id="bc7c9-166">En el panel de navegación izquierdo, haga clic en **búsqueda &amp; búsqueda de contenido de investigación >**.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-166">In the left navigation, click **Search &amp; Investigation > Content search**.</span></span>
    
13. <span data-ttu-id="bc7c9-167">Haga clic en el icono de signo más para agregar una búsqueda.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-167">Click the plus icon to add a search.</span></span>
    
14. <span data-ttu-id="bc7c9-168">En la ventana **Nueva búsqueda**, escriba **Búsqueda de contrato de Tailspin** en **Nombre**.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-168">In the **New search** window, type **Tailspin contract search** in **Name**.</span></span>
    
15. <span data-ttu-id="bc7c9-169">En **¿Dónde desea que busquemos?**, haga clic en **Buscar en todas partes,** seleccione **Exchange**, **SharePoint** y **Carpetas públicas** y, a continuación, haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-169">In **Where do you want us to look?**, click **Search everywhere,** select **Exchange**, **SharePoint**, and **Public Folders**, and then click **Next.**</span></span>
    
16. <span data-ttu-id="bc7c9-170">En **¿Dónde desea que busquemos?**, escriba **Contrato de Tailspin** y, a continuación, haga clic en **Buscar**.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-170">In **What do you want us to look for?**, type **Tailspin contract**, and then click **Search**.</span></span>
    
17. <span data-ttu-id="bc7c9-171">En la lista de búsquedas, haga clic en el nombre de **Búsqueda de contrato de Tailspin**.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-171">In the list of searches, click the **Tailspin contract search** name.</span></span>
    
18. <span data-ttu-id="bc7c9-p105">En el panel de **búsqueda de contrato Tailspin** , haga clic en **vista previa de resultados de búsqueda** en **los resultados**. Debería ver una ventana con una lista de los dos documentos en el sitio de SharePoint de producción ( **documento** y **Documento1**) y los mensajes de **correo electrónico de prueba 1** y **prueba de correo electrónico 3** a User6. Cierre la ventana.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-p105">In the **Tailspin contract search** pane, click **Preview search results** under **Results**. You should see a window listing the two documents on the Production SharePoint site ( **Document** and **Document1**) and the **Test email 1** and **Test email 3** emails to User6. Close the window.</span></span>
    
19. <span data-ttu-id="bc7c9-175">En el panel **Búsqueda de contenido**, en **Analizar resultados con exhibición avanzada de documentos electrónicos**, haga clic en **Vista previa de resultados para análisis**.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-175">In the **Content search** pane, under **Analyze results with Advanced eDiscovery**, click **Preview results for analysis**.</span></span>
    
20. <span data-ttu-id="bc7c9-176">En la ventana **Preparar los resultados de búsqueda para la búsqueda de contrato de Tailspin**, haga clic en **Preparar** y espere a que finalice.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-176">In the **Prepare the search results for Tailspin contract search** window, click **Prepare** and wait for it to complete.</span></span>
    
<span data-ttu-id="bc7c9-177">En este procedimiento, creará un nuevo caso de exhibición avanzada de documentos electrónicos y analizará los resultados de la búsqueda del contrato de Tailspin.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-177">In this procedure, you create a new case for Advanced eDiscovery and analyze the Tailspin contract search results.</span></span>
  
1. <span data-ttu-id="bc7c9-178">En el panel de navegación izquierdo, haga clic en la **exhibición de documentos electrónicos** en **búsqueda &amp; investigación**.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-178">In the left navigation, click **eDiscovery** under **Search &amp; Investigation**.</span></span>
    
2. <span data-ttu-id="bc7c9-179">En el panel **Exhibición de documentos electrónicos**, haga clic en **Ir a exhibición avanzada de documentos electrónicos**.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-179">In the **eDiscovery** pane, click **Go to Advanced eDiscovery**.</span></span>
    
3. <span data-ttu-id="bc7c9-180">En la pestaña **Exhibición avanzada de documentos electrónicos**, haga clic en el icono de signo más para agregar un nuevo caso.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-180">In the **Advanced eDiscovery** tab, click the plus icon to add a new case.</span></span>
    
4. <span data-ttu-id="bc7c9-p106">	En el panel *\*Agregar caso*\*, escriba *\*Disputa contractual de Tailspin** en *\*Nombre** y, a continuación, haga clic en *\*Aceptar*\*. Espere a que se cree el caso.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-p106">In the **Add case** pane, type **Tailspin contract dispute** in **Name**, and then click **OK**. Wait for the case to be created.</span></span>
    
5. <span data-ttu-id="bc7c9-183">Haga doble clic en el caso **Disputa contractual de Tailspin** de la lista. </span><span class="sxs-lookup"><span data-stu-id="bc7c9-183">Double click the **Tailspin contract dispute** case in the list.</span></span>
    
6. <span data-ttu-id="bc7c9-p107">En la lista de **contenedor** , haga clic en el contenedor de **búsqueda de Tailspin contrato** y, a continuación, haga clic en **proceso**. Espere a que el procesamiento para llevar a cabo.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-p107">In the **Container** list, click the **Tailspin contract search** container, and then click **Process**. Wait for the processing to complete.</span></span>
    
7. <span data-ttu-id="bc7c9-186">Cuando **Proceso: completado** aparezca en la parte inferior de la ventana, haga clic en **Resumen de proceso** en la navegación izquierda para ver un resumen.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-186">When **Process: completed** appears at the bottom of the window, click **Process summary** in the left navigation to see a summary.</span></span>
    
8. <span data-ttu-id="bc7c9-187">En la navegación superior, haga clic en **Analizar**.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-187">In the top navigation, click **Analyze**.</span></span>
    
9. <span data-ttu-id="bc7c9-188">En la página **Configuración**, en **Temas**, escriba **3** en **Número máximo de temas**.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-188">On the **Setup** page, under **Themes**, type **3** in **Max number of themes**.</span></span>
    
10. <span data-ttu-id="bc7c9-p108">Haga clic en **analizar** y espere a que el análisis para llevar a cabo. Debería ver una serie de gráficos circulares con el análisis de la población de destino, documentos, mensajes de correo electrónico y los datos adjuntos. Para obtener más información, vea [los resultados de la visualización de analizar](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).</span><span class="sxs-lookup"><span data-stu-id="bc7c9-p108">Click **Analyze** and wait for the analysis to complete. You should see a series of pie charts with analysis of the target population, documents, emails, and attachments. For more information, see [Viewing Analyze results](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).</span></span>
    
<span data-ttu-id="bc7c9-192">Ahora puede utilizar este entorno para crear nuevo contenido, nuevas búsquedas y casos, además de experimentar con la exhibición avanzada de documentos electrónicos en Office 365.</span><span class="sxs-lookup"><span data-stu-id="bc7c9-192">You can now use this environment to create new content, new searches and cases, and experiment further with Advanced eDiscovery in Office 365.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="bc7c9-193">Vea también</span><span class="sxs-lookup"><span data-stu-id="bc7c9-193">See Also</span></span>

[<span data-ttu-id="bc7c9-194">Guías del laboratorio de pruebas de adopción de la nube (TLG)</span><span class="sxs-lookup"><span data-stu-id="bc7c9-194">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="bc7c9-195">Entorno de desarrollo y pruebas de la configuración básica</span><span class="sxs-lookup"><span data-stu-id="bc7c9-195">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="bc7c9-196">Entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="bc7c9-196">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="bc7c9-197">Sincronización de directorios (DirSync) para el entorno de desarrollo y prueba de Office 365</span><span class="sxs-lookup"><span data-stu-id="bc7c9-197">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="bc7c9-198">Seguridad de Cloud App para su entorno de desarrollo y prueba de Office 365</span><span class="sxs-lookup"><span data-stu-id="bc7c9-198">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="bc7c9-199">Adopción de la nube y soluciones híbridas</span><span class="sxs-lookup"><span data-stu-id="bc7c9-199">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="bc7c9-200">eDiscovery avanzado de Office 365</span><span class="sxs-lookup"><span data-stu-id="bc7c9-200">Office 365 Advanced eDiscovery</span></span>](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


