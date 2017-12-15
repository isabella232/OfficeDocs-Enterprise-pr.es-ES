---
title: "Etiquetado y clasificación de datos en el entorno de desarrollo y pruebas de Office 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- jan17entnews
- TLG
- Ent_TLGs
ms.assetid: 919b8fc7-b0bc-46db-91f5-37342564e01b
description: "Resumen: Configurar y demostrar la clasificación de datos y etiquetado utilizando al cliente de protección de información de Azure (AIP) en el entorno de desarrollo y prueba de Office 365."
ms.openlocfilehash: 2784f4105903855de89c6c45f7a643279bb4dfbf
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2017
---
# <a name="data-classification-and-labeling-in-the-office-365-devtest-environment"></a><span data-ttu-id="4d1bf-103">Etiquetado y clasificación de datos en el entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="4d1bf-103">Data classification and labeling in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="4d1bf-104">**Resumen:** Configurar y demostrar la clasificación de datos y etiquetado utilizando al cliente de protección de información de Azure (AIP) en el entorno de desarrollo y prueba de Office 365.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-104">**Summary:** Configure and demonstrate data classification and labeling using the Azure Information Protection (AIP) client in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="4d1bf-p101">El cliente de protección de la información de Azure permite clasificar un documento antes de cargarlo en una carpeta de SharePoint Online en Office 365. Con las instrucciones de este artículo, instale al cliente de protección de la información de Azure y demostrar la clasificación de datos. Para obtener más información, consulte [Protección de la información de Azure](https://www.microsoft.com/cloud-platform/azure-information-protection).</span><span class="sxs-lookup"><span data-stu-id="4d1bf-p101">The Azure Information Protection client allows you to classify a document before you upload it to a SharePoint Online folder in Office 365. With the instructions in this article, you install the Azure Information Protection client and demonstrate data classification. For more information, see [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection).</span></span>
  
> [!TIP]
> <span data-ttu-id="4d1bf-108">Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual para todos los artículos de la pila de una guía de laboratorio de prueba de nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="4d1bf-109">Fase 1: Crear el entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="4d1bf-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="4d1bf-110">Siga las instrucciones en el [entorno de desarrollo y prueba de Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="4d1bf-110">Follow the instructions in [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
## <a name="phase-2-add-the-azure-information-protection-trial-subscription"></a><span data-ttu-id="4d1bf-111">Fase 2: Agregar la suscripción de prueba de Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="4d1bf-111">Phase 2: Add the Azure Information Protection trial subscription</span></span>

<span data-ttu-id="4d1bf-p102">En esta fase, agregue Azure protección de la información para su entorno de pruebas y desarrollo de Office 365 y habilitarlo para las cuentas de usuario. Si ha configurado el [entorno de pruebas y desarrollo de EMS y Office 365](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx), omita esta fase. La suscripción de prueba de Enterprise Mobility Suite incluye licencias de protección de la información de Azure.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-p102">In this phase, you add Azure Information Protection to your Office 365 dev/test environment and enable it for your user accounts. If you have configured the [Office 365 and EMS dev/test environment](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx), skip this phase. The Enterprise Mobility Suite trial subscription includes Azure Information Protection licenses.</span></span>
  
<span data-ttu-id="4d1bf-115">Primero, regístrese para obtener una suscripción de prueba de Azure Information Protection.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-115">First, sign up for an Azure Information Protection trial subscription.</span></span>
  
### <a name="sign-up-for-an-azure-information-protection-trial-subscription"></a><span data-ttu-id="4d1bf-116">Registrarse para obtener una suscripción de prueba de Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="4d1bf-116">Sign up for an Azure Information Protection trial subscription</span></span>

1. <span data-ttu-id="4d1bf-117">En Internet Explorer o el explorador, vaya a [http://portal.office.com](http://portal.office.com) e iniciar sesión con su cuenta de administrador global de Office 365.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-117">In Internet Explorer or your browser, go to [http://portal.office.com](http://portal.office.com) and sign in with your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="4d1bf-118">En la ficha **Página de inicio de Microsoft Office** , haga clic en el mosaico de **Admin** .</span><span class="sxs-lookup"><span data-stu-id="4d1bf-118">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="4d1bf-119">En la ficha administración de Office 365, la navegación de la izquierda, haga clic en **de facturación > adquirir servicios**.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-119">On the Office 365 Admin tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="4d1bf-p103">En la página **Servicios de compra** , busque el elemento de **Azure información protección Premium P2** . Coloca el ratón sobre él y haga clic en **iniciar la versión de prueba gratuita**.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-p103">On the **Purchase services** page, find the **Azure Information Protection Premium P2** item. Hover your mouse over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="4d1bf-122">En la página **confirmar su pedido** , haga clic en **Probar ahora**.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-122">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="4d1bf-123">En la página de **confirmación del pedido** , haga clic en **continuar**.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-123">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="4d1bf-124">Después, habilite la licencia de Azure Information Protection para todas las cuentas de usuario.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-124">Next, you enable the Azure Information Protection license for all user accounts.</span></span>
  
1. <span data-ttu-id="4d1bf-125">En la ficha de centro de administración de Office 365, haga clic en **usuarios**.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-125">On the Office 365 admin center tab, click **Users**.</span></span>
    
2.  <span data-ttu-id="4d1bf-126">En la lista de cuentas de usuario, seleccione la cuenta de administrador global y, a continuación, haga clic en **Editar** para **licencias de producto**.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-126">In the list of user accounts, select your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="4d1bf-127">Activar la licencia del producto para **Azure información protección Premium P2** a **en**, haga clic en **Guardar** y, a continuación, haga clic en **Cerrar** dos veces.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-127">Turn the product license for **Azure Information Protection Premium P2** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="4d1bf-128">Repita los pasos 2 y 3 para las demás cuentas de usuario (del Usuario 1 al Usuario 5).</span><span class="sxs-lookup"><span data-stu-id="4d1bf-128">Repeat steps 2 and 3 for your other user accounts (User 1 through User 5).</span></span>
    
<span data-ttu-id="4d1bf-129">Ahora su entorno de desarrollo y pruebas de Office 365 tiene:</span><span class="sxs-lookup"><span data-stu-id="4d1bf-129">Your Office 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="4d1bf-130">Suscripciones de prueba de Azure Information Protection y de Office 365 E5 Enterprise.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-130">Office 365 E5 Enterprise and Azure Information Protection trial subscriptions.</span></span>
    
- <span data-ttu-id="4d1bf-131">Todas las cuentas de usuario habilitadas para usar Office 365 E5 Enterprise y Azure Information Protection.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-131">All of your user accounts enabled to use both Office 365 E5 Enterprise and Azure Information Protection.</span></span>
    
## <a name="phase-3-demonstrate-data-classification"></a><span data-ttu-id="4d1bf-132">Fase 3: Mostrar la clasificación de datos</span><span class="sxs-lookup"><span data-stu-id="4d1bf-132">Phase 3: Demonstrate data classification</span></span>

<span data-ttu-id="4d1bf-133">En esta fase, muestra la clasificación de datos con el cliente de Azure Information Protection y la directiva de Azure Information Protection predeterminada.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-133">In this phase, you demonstrate data classification using the Azure Information Protection client and the default Azure Information Protection policy.</span></span>
  
<span data-ttu-id="4d1bf-134">Si está usando el entorno de desarrollo y pruebas de una empresa simulada de Office 365, debe instalar primero Office 2016 en CLIENTE1.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-134">If you are using the simulated enterprise Office 365 dev/test environment, you must first install Office 2016 on CLIENT1.</span></span>
  
1. <span data-ttu-id="4d1bf-135">Utilice el explorador y vaya al [portal de Azure](http://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="4d1bf-135">Use your browser and go to the [Azure portal](http://portal.azure.com).</span></span>
    
2. <span data-ttu-id="4d1bf-136">Haga clic en **grupos de recursos >** [nombre de grupo de los recursos] **> CLIENTE1 > conectar**.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-136">Click **Resource Groups >** [your resource group name] **> CLIENT1 > Connect**.</span></span>
    
3. <span data-ttu-id="4d1bf-137">Desde CLIENTE1, ejecute Internet Explorer, visite el portal de Office en [http://portal.office.com](http://portal.office.com)y, a continuación, inicie sesión con el nombre de la cuenta usuario5 y la contraseña.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-137">From CLIENT1, run Internet Explorer, go to the Office portal at [http://portal.office.com](http://portal.office.com), and then sign in with the User5 account name and password.</span></span>
    
4. <span data-ttu-id="4d1bf-138">En la ficha **Página de inicio de Microsoft Office** , haga clic en **instalar Office 2016**.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-138">On the **Microsoft Office Home** tab, click **Install Office 2016**.</span></span>
    
5. <span data-ttu-id="4d1bf-p104">Ejecute la descarga cuando se le pida y haga clic en **Sí** cuando se lo pida Control de cuentas de usuario. Espere a que Office instalar. Cuando haya terminado, haga clic **Cerrar** dos veces.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-p104">Run the download when prompted and click **Yes** when prompted by User Account Control. Wait for Office to install. When complete, click **Close** twice.</span></span>
    
<span data-ttu-id="4d1bf-142">Después, instale el cliente de Azure Information Protection.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-142">Next, you install the Azure Information Protection client.</span></span>
  
1. <span data-ttu-id="4d1bf-143">En el explorador o Internet Explorer, vaya a la [página de descarga de Microsoft Azure protección de la información](https://www.microsoft.com/download/details.aspx?id=53018).</span><span class="sxs-lookup"><span data-stu-id="4d1bf-143">In your browser or Internet Explorer, go to the [Microsoft Azure Information Protection download page](https://www.microsoft.com/download/details.aspx?id=53018).</span></span>
    
  - <span data-ttu-id="4d1bf-144">Si está usando la versión ligera del entorno de desarrollo y pruebas de Office 365, use el explorador en su equipo local.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-144">If you are using the lightweight version of the Office 365 dev/test environment, use the browser on your local computer.</span></span>
    
  - <span data-ttu-id="4d1bf-145">Si está usando el entorno de desarrollo y pruebas de una empresa simulada de Office 365, ejecute Internet Explorer desde CLIENTE1.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-145">If you are using the simulated enterprise Office 365 dev/test environment, run Internet Explorer from CLIENT1.</span></span>
    
2. <span data-ttu-id="4d1bf-146">En la página de descarga de **Microsoft Azure protección de la información** , haga clic en **Descargar**, haga clic en **AzInfoProtection.exe**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-146">On the **Microsoft Azure Information Protection** download page, click **Download**, click **AzInfoProtection.exe**, and then click **Next**.</span></span>
    
3. <span data-ttu-id="4d1bf-147">Cuando se le solicite, ejecute AzInfoProtection.exe.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-147">When prompted, run AzInfoProtection.exe.</span></span>
    
4. <span data-ttu-id="4d1bf-148">En el cuadro cliente **instalar la protección de la información de Azure** , haga clic en **Acepto**y, a continuación, haga clic en **Sí** cuando se lo pida Control de cuentas de usuario.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-148">In the **Install the Azure Information Protection** client box, click **I agree**, and then click **Yes** when prompted by User Account Control.</span></span>
    
5. <span data-ttu-id="4d1bf-149">En el cuadro **finalizado correctamente** , haga clic en **Cerrar.**</span><span class="sxs-lookup"><span data-stu-id="4d1bf-149">In the **Completed successfully** box, click **Close.**</span></span>
    
<span data-ttu-id="4d1bf-150">Después, muestre la clasificación de documentos.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-150">Next, you demonstrate document classification.</span></span>
  
1. <span data-ttu-id="4d1bf-151">Haga clic en el icono de **Word** en la barra de tareas.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-151">Click the **Word** icon in the taskbar.</span></span>
    
2. <span data-ttu-id="4d1bf-152">Cuando se le solicite, inicie sesión con el nombre de cuenta Usuario5 y la contraseña.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-152">When prompted, sign in with the User5 account name and password.</span></span>
    
3. <span data-ttu-id="4d1bf-153">Si acaba de instalar Office 2016 en CLIENTE1, en el **primero lo primer** cuadro, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-153">If you just installed Office 2016 on CLIENT1, in the **First things first** box, click **Accept**.</span></span>
    
4. <span data-ttu-id="4d1bf-154">Haga clic en **documento en blanco**.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-154">Click **Blank document**.</span></span> 
    
    <span data-ttu-id="4d1bf-155">Tenga en cuenta la sección de **protección** de la cinta de opciones en la ficha **Inicio** y en la fila de las clasificaciones de documento.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-155">Note the **Protection** section of the ribbon on the **Home** tab and the row of document classifications.</span></span>
    
5. <span data-ttu-id="4d1bf-156">En el documento en blanco, escriba algunas palabras.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-156">In the blank document, type some text.</span></span>
    
6. <span data-ttu-id="4d1bf-157">Haga clic en **archivo > Guardar**, escriba el nombre **BeforeAIP**y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-157">Click **File > Save**, type the name **BeforeAIP**, and then click **OK**.</span></span> 
    
7. <span data-ttu-id="4d1bf-158">En la fila de clases de documento, haga clic en la flecha hacia abajo para el **secreto**y, a continuación, haga clic en **Empresa todo**.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-158">In the row of document classes, click the down arrow for **Secret**, and then click **All Company**.</span></span>
    
8. <span data-ttu-id="4d1bf-159">Haga clic en **archivo > Guardar como**, escriba el nombre **AfterAIP**y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-159">Click **File > Save As**, type the name **AfterAIP**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="4d1bf-160">Haga clic en **Explorador de archivos** en la barra de tareas y, a continuación, abra la carpeta **documentos** .</span><span class="sxs-lookup"><span data-stu-id="4d1bf-160">Click **File Explorer** in the taskbar, and then open the **Documents** folder.</span></span>
    
    <span data-ttu-id="4d1bf-p105">Tenga en cuenta los diferentes tamaños de los documentos **BeforeAIP** y **AfterAIP** . El documento AfterAIP es mayor porque contiene la información de clasificación.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-p105">Note the different file sizes of the **BeforeAIP** and **AfterAIP** documents. The AfterAIP document is larger because it contains the classification information.</span></span>
    
<span data-ttu-id="4d1bf-163">Después, permita que todos los usuarios tengan acceso a la colección de sitios de soporte.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-163">Next, you allow everyone to access the Support site collection.</span></span>
  
1. <span data-ttu-id="4d1bf-164">En la ficha **Página de inicio de Microsoft Office** , haga clic en **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-164">On the **Microsoft Office Home** tab, click **SharePoint**.</span></span>
    
2. <span data-ttu-id="4d1bf-165">Desde la ficha de **SharePoint** , haga clic en la **colección de sitios de soporte técnico**.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-165">From the **SharePoint** tab, click **Support site collection**.</span></span>
    
3. <span data-ttu-id="4d1bf-166">En la parte superior derecha, haga clic en el icono de **configuración** y, a continuación, haga clic en **compartido con**.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-166">In the upper right, click the **Settings** icon, and then click **Shared with**.</span></span>
    
4. <span data-ttu-id="4d1bf-167">En el **recurso compartido 'Colección de sitios de soporte'**, haga clic en **Avanzadas**.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-167">In **Share 'Support site collection'**, click **Advanced**.</span></span>
    
5. <span data-ttu-id="4d1bf-168">En la lista de grupos de SharePoint, haga clic en **los miembros de colección de sitios de soporte técnico**.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-168">In the list of SharePoint groups, click **Support site collection Members**.</span></span>
    
6. <span data-ttu-id="4d1bf-169">En la página **personas y grupos** , haga clic en **nuevo**.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-169">On the **People and Groups** page, click **New**.</span></span>
    
7. <span data-ttu-id="4d1bf-170">En el **recurso compartido 'Colección de sitios de soporte'**, escriba **todos**, haga clic en **todos excepto los usuarios externos**y, a continuación, haga clic en **Share.**</span><span class="sxs-lookup"><span data-stu-id="4d1bf-170">In **Share 'Support site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share.**</span></span>
    
8. <span data-ttu-id="4d1bf-171">Cierre la ficha **usuarios y grupos** .</span><span class="sxs-lookup"><span data-stu-id="4d1bf-171">Close the **People and Groups** tab.</span></span>
    
<span data-ttu-id="4d1bf-172">Después, inicie sesión con su cuenta Usuario5 y cargue el documento protegido por AIP a la carpeta Documentos de la colección de sitios de soporte.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-172">Next, you sign in with your User5 account and upload the AIP-protected document to the Documents folder of the Support site collection.</span></span>
  
1. <span data-ttu-id="4d1bf-173">En la ficha **Página de inicio de Microsoft Office** , en la parte superior derecha, haga clic en el icono de usuario y, a continuación, haga clic en **Cerrar sesión**.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-173">On the **Microsoft Office Home** tab, in the upper right, click the user icon, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="4d1bf-174">Vaya a [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="4d1bf-174">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="4d1bf-175">En el ** iniciar una sesión en Office 365 ** de página, haga clic en el nombre de la cuenta usuario5 e identifícate.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-175">On the ** Office 365 sign in** page, click the User5 account name and sign in.</span></span>
    
4. <span data-ttu-id="4d1bf-176">En la ficha **Página de inicio de Microsoft Office** , haga clic en **SharePoint > compatible con la colección de sitios**.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-176">On the **Microsoft Office Home** tab, click **SharePoint > Support site collection**.</span></span>
    
5. <span data-ttu-id="4d1bf-177">Haga clic en **documentos**, haga clic en **cargar**, haga clic en el documento de **AfterAIP** y, a continuación, haga clic en **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-177">Click **Documents**, click **Upload**, click the **AfterAIP** document, and then click **Open**.</span></span>
    
    <span data-ttu-id="4d1bf-178">Debe ver el documento AfterAIP.docx en la carpeta Documentos de la colección de sitios de soporte.</span><span class="sxs-lookup"><span data-stu-id="4d1bf-178">You should see AfterAIP.docx in the Documents folder on the Support site collection.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="4d1bf-179">See Also</span><span class="sxs-lookup"><span data-stu-id="4d1bf-179">See Also</span></span>

[<span data-ttu-id="4d1bf-180">Guías del laboratorio de pruebas de adopción de la nube (TLG)</span><span class="sxs-lookup"><span data-stu-id="4d1bf-180">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="4d1bf-181">Office 365 y entorno de desarrollo y prueba de EMS</span><span class="sxs-lookup"><span data-stu-id="4d1bf-181">Office 365 and EMS dev/test environment</span></span>](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)
  
[<span data-ttu-id="4d1bf-182">Protección de la información de Azure</span><span class="sxs-lookup"><span data-stu-id="4d1bf-182">Azure Information Protection</span></span>](https://www.microsoft.com/cloud-platform/azure-information-protection)


