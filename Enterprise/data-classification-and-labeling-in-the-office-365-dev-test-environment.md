---
title: Etiquetado y clasificación de datos en el entorno de desarrollo y pruebas de Office 365
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
ms.assetid: 919b8fc7-b0bc-46db-91f5-37342564e01b
description: 'Resumen: Configurar y mostrar el etiquetado y la clasificación de datos con el cliente de Azure Information Protection (AIP) en el entorno de desarrollo y pruebas de Office 365.'
ms.openlocfilehash: ff8533cc6f1a5a34335f6ea469f7a8ec0a6be4da
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "30573964"
---
# <a name="data-classification-and-labeling-in-the-office-365-devtest-environment"></a><span data-ttu-id="35611-103">Etiquetado y clasificación de datos en el entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="35611-103">Data classification and labeling in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="35611-104">**Resumen:** Configurar y mostrar el etiquetado y la clasificación de datos con el cliente de Azure Information Protection (AIP) en el entorno de desarrollo y pruebas de Office 365.</span><span class="sxs-lookup"><span data-stu-id="35611-104">**Summary:** Configure and demonstrate data classification and labeling using the Azure Information Protection (AIP) client in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="35611-105">El cliente de Azure Information Protection le permite clasificar un documento antes de cargarlo en una carpeta de SharePoint Online en Office 365.</span><span class="sxs-lookup"><span data-stu-id="35611-105">The Azure Information Protection client lets you classify a document before you upload it to a SharePoint Online folder in Office 365.</span></span> <span data-ttu-id="35611-106">Con las instrucciones de este artículo, puede instalar el cliente de Azure Information Protection y mostrar la clasificación de datos.</span><span class="sxs-lookup"><span data-stu-id="35611-106">With the instructions in this article, you install the Azure Information Protection client and demonstrate data classification.</span></span> <span data-ttu-id="35611-107">Para obtener más información, consulte [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection).</span><span class="sxs-lookup"><span data-stu-id="35611-107">For more information, see [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection).</span></span>
  
> [!TIP]
> <span data-ttu-id="35611-108">Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual de todos los artículos de la pila Guía de laboratorio de pruebas de One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="35611-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="35611-109">Fase 1: Crear el entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="35611-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="35611-110">Siga las instrucciones de [Office 365 dev/test environment](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="35611-110">Follow the instructions in [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
## <a name="phase-2-add-the-azure-information-protection-trial-subscription"></a><span data-ttu-id="35611-111">Fase 2: Agregar la suscripción de prueba de Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="35611-111">Phase 2: Add the Azure Information Protection trial subscription</span></span>

<span data-ttu-id="35611-112">En esta fase, agregue Azure Information Protection a su entorno de desarrollo y pruebas de Office 365 y habilítelo para sus cuentas de usuario.</span><span class="sxs-lookup"><span data-stu-id="35611-112">In this phase, you add Azure Information Protection to your Office 365 dev/test environment and enable it for your user accounts.</span></span> <span data-ttu-id="35611-113">Si ha configurado el [Office 365 and EMS dev/test environment](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx), omita esta fase.</span><span class="sxs-lookup"><span data-stu-id="35611-113">If you have configured the [Office 365 and EMS dev/test environment](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx), skip this phase.</span></span> <span data-ttu-id="35611-114">La suscripción de prueba de Enterprise Mobility Suite incluye licencias de Azure Information Protection.</span><span class="sxs-lookup"><span data-stu-id="35611-114">The Enterprise Mobility Suite trial subscription includes Azure Information Protection licenses.</span></span>
  
<span data-ttu-id="35611-115">Primero, regístrese para obtener una suscripción de prueba de Azure Information Protection.</span><span class="sxs-lookup"><span data-stu-id="35611-115">First, sign up for an Azure Information Protection trial subscription.</span></span>
  
### <a name="sign-up-for-an-azure-information-protection-trial-subscription"></a><span data-ttu-id="35611-116">Registrarse para obtener una suscripción de prueba de Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="35611-116">Sign up for an Azure Information Protection trial subscription</span></span>

1. <span data-ttu-id="35611-117">En Internet Explorer o en su explorador, vaya [http://admin.microsoft.com](http://admin.microsoft.com) a e inicie sesión con su cuenta de administrador global de Office 365.</span><span class="sxs-lookup"><span data-stu-id="35611-117">In Internet Explorer or your browser, go to [http://admin.microsoft.com](http://admin.microsoft.com) and sign in with your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="35611-118">En la pestaña **Página principal de Microsoft Office**, haga clic en el icono de **Administración**.</span><span class="sxs-lookup"><span data-stu-id="35611-118">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="35611-119">En la pestaña Administración de Office 365, en el panel de navegación izquierdo, haga clic en **Facturación > Servicios de compra**.</span><span class="sxs-lookup"><span data-stu-id="35611-119">On the Office 365 Admin tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="35611-p103">En la página **Servicios de compra**, busque el elemento **Azure Information Protection Premium P2**. Mueva el puntero sobre el elemento y haga clic en **Iniciar prueba gratuita**.</span><span class="sxs-lookup"><span data-stu-id="35611-p103">On the **Purchase services** page, find the **Azure Information Protection Premium P2** item. Hover your mouse over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="35611-122">En la página **Confirmar pedido**, haga clic en **Probar ahora**.</span><span class="sxs-lookup"><span data-stu-id="35611-122">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="35611-123">En la página **Recibo del pedido**, haga clic en **Continuar**.</span><span class="sxs-lookup"><span data-stu-id="35611-123">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="35611-124">Después, habilite la licencia de Azure Information Protection para todas las cuentas de usuario.</span><span class="sxs-lookup"><span data-stu-id="35611-124">Next, you enable the Azure Information Protection license for all user accounts.</span></span>
  
1. <span data-ttu-id="35611-125">En la pestaña Centro de administración de 365 de Microsoft, haga clic en **usuarios**.</span><span class="sxs-lookup"><span data-stu-id="35611-125">On the Microsoft 365 admin center tab, click **Users**.</span></span>
    
2.  <span data-ttu-id="35611-126"> En la lista de cuentas de usuario, seleccione la cuenta del administrador global y, después, haga clic en *\*Editar** para *\*Licencias de productos*\*.</span><span class="sxs-lookup"><span data-stu-id="35611-126">In the list of user accounts, select your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="35611-127">	Establezca la licencia de producto de *\*Azure Information Protection Premium P2** en *\*Activada*\*, haga clic en *\*Guardar** y, después, haga clic en *\*Cerrar** dos veces.</span><span class="sxs-lookup"><span data-stu-id="35611-127">Turn the product license for **Azure Information Protection Premium P2** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="35611-128">Repita los pasos 2 y 3 para las demás cuentas de usuario (del Usuario 1 al Usuario 5).</span><span class="sxs-lookup"><span data-stu-id="35611-128">Repeat steps 2 and 3 for your other user accounts (User 1 through User 5).</span></span>
    
<span data-ttu-id="35611-129">Ahora su entorno de desarrollo y pruebas de Office 365 tiene:</span><span class="sxs-lookup"><span data-stu-id="35611-129">Your Office 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="35611-130">Suscripciones de prueba de Azure Information Protection y de Office 365 E5 Enterprise.</span><span class="sxs-lookup"><span data-stu-id="35611-130">Office 365 E5 Enterprise and Azure Information Protection trial subscriptions.</span></span>
    
- <span data-ttu-id="35611-131">Todas las cuentas de usuario habilitadas para usar Office 365 E5 Enterprise y Azure Information Protection.</span><span class="sxs-lookup"><span data-stu-id="35611-131">All of your user accounts enabled to use both Office 365 E5 Enterprise and Azure Information Protection.</span></span>
    
## <a name="phase-3-demonstrate-data-classification"></a><span data-ttu-id="35611-132">Fase 3: Mostrar la clasificación de datos</span><span class="sxs-lookup"><span data-stu-id="35611-132">Phase 3: Demonstrate data classification</span></span>

<span data-ttu-id="35611-133">En esta fase, muestra la clasificación de datos con el cliente de Azure Information Protection y la directiva de Azure Information Protection predeterminada.</span><span class="sxs-lookup"><span data-stu-id="35611-133">In this phase, you demonstrate data classification using the Azure Information Protection client and the default Azure Information Protection policy.</span></span>
  
<span data-ttu-id="35611-134">Si está usando el entorno de desarrollo y pruebas de una empresa simulada de Office 365, debe instalar primero Office 2016 en CLIENTE1.</span><span class="sxs-lookup"><span data-stu-id="35611-134">If you are using the simulated enterprise Office 365 dev/test environment, you must first install Office 2016 on CLIENT1.</span></span>
  
1. <span data-ttu-id="35611-135">Use el explorador y vaya a [Azure portal](http://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="35611-135">Use your browser and go to the [Azure portal](http://portal.azure.com).</span></span>
    
2. <span data-ttu-id="35611-136">	Haga clic en *\*Grupos de recursos** [el nombre del grupo de recursos] *\*> CLIENTE1 > Conectar*\*.</span><span class="sxs-lookup"><span data-stu-id="35611-136">Click **Resource Groups >** [your resource group name] **> CLIENT1 > Connect**.</span></span>
    
3. <span data-ttu-id="35611-137">Desde cliente1, ejecute Internet Explorer, vaya al portal de Office en [http://admin.microsoft.com](http://admin.microsoft.com)y, a continuación, inicie sesión con el nombre de cuenta usuario5 y la contraseña.</span><span class="sxs-lookup"><span data-stu-id="35611-137">From CLIENT1, run Internet Explorer, go to the Office portal at [http://admin.microsoft.com](http://admin.microsoft.com), and then sign in with the User5 account name and password.</span></span>
    
4. <span data-ttu-id="35611-138">	En la pestaña *\*Página principal de Microsoft Office*\*, haga clic en *\*Instalar Office 2016*\*.</span><span class="sxs-lookup"><span data-stu-id="35611-138">On the **Microsoft Office Home** tab, click **Install Office 2016**.</span></span>
    
5. <span data-ttu-id="35611-p104">	Ejecute la descarga cuando se le solicite y haga clic en *\*Sí** cuando se lo pida el Control de cuentas de usuario. Espere a que Office se instale. Una vez completado el proceso, haga clic en *\*Cerrar** dos veces.</span><span class="sxs-lookup"><span data-stu-id="35611-p104">Run the download when prompted and click **Yes** when prompted by User Account Control. Wait for Office to install. When complete, click **Close** twice.</span></span>
    
<span data-ttu-id="35611-142">Después, instale el cliente de Azure Information Protection.</span><span class="sxs-lookup"><span data-stu-id="35611-142">Next, you install the Azure Information Protection client.</span></span>
  
1. <span data-ttu-id="35611-143">En el explorador o en Internet Explorer, vaya a la [Página de descarga de Microsoft Azure Information Protection](https://www.microsoft.com/download/details.aspx?id=53018).</span><span class="sxs-lookup"><span data-stu-id="35611-143">In your browser or Internet Explorer, go to the [Microsoft Azure Information Protection download page](https://www.microsoft.com/download/details.aspx?id=53018).</span></span>
    
  - <span data-ttu-id="35611-144">Si está usando la versión ligera del entorno de desarrollo y pruebas de Office 365, use el explorador en su equipo local.</span><span class="sxs-lookup"><span data-stu-id="35611-144">If you are using the lightweight version of the Office 365 dev/test environment, use the browser on your local computer.</span></span>
    
  - <span data-ttu-id="35611-145">Si está usando el entorno de desarrollo y pruebas de una empresa simulada de Office 365, ejecute Internet Explorer desde CLIENTE1.</span><span class="sxs-lookup"><span data-stu-id="35611-145">If you are using the simulated enterprise Office 365 dev/test environment, run Internet Explorer from CLIENT1.</span></span>
    
2. <span data-ttu-id="35611-146">En la página de descarga de **Microsoft Azure Information Protection**, haga clic en **Descargar**, en **AzInfoProtection.exe** y, después, en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="35611-146">On the **Microsoft Azure Information Protection** download page, click **Download**, click **AzInfoProtection.exe**, and then click **Next**.</span></span>
    
3. <span data-ttu-id="35611-147">Cuando se le solicite, ejecute AzInfoProtection.exe.</span><span class="sxs-lookup"><span data-stu-id="35611-147">When prompted, run AzInfoProtection.exe.</span></span>
    
4. <span data-ttu-id="35611-148">En el cuadro **Instalar el cliente de Azure Information Protection**, haga clic en **Acepto** y, después, en **Sí** cuando se lo pida el Control de cuentas de usuario.</span><span class="sxs-lookup"><span data-stu-id="35611-148">In the **Install the Azure Information Protection** client box, click **I agree**, and then click **Yes** when prompted by User Account Control.</span></span>
    
5. <span data-ttu-id="35611-149">En el cuadro **Completado correctamente**, haga clic en **Cerrar**.</span><span class="sxs-lookup"><span data-stu-id="35611-149">In the **Completed successfully** box, click **Close.**</span></span>
    
<span data-ttu-id="35611-150">Después, muestre la clasificación de documentos.</span><span class="sxs-lookup"><span data-stu-id="35611-150">Next, you demonstrate document classification.</span></span>
  
1. <span data-ttu-id="35611-151">Haga clic en el icono **Word** en la barra de tareas.</span><span class="sxs-lookup"><span data-stu-id="35611-151">Click the **Word** icon in the taskbar.</span></span>
    
2. <span data-ttu-id="35611-152">Cuando se le solicite, inicie sesión con el nombre de cuenta Usuario5 y la contraseña.</span><span class="sxs-lookup"><span data-stu-id="35611-152">When prompted, sign in with the User5 account name and password.</span></span>
    
3. <span data-ttu-id="35611-153">Si acaba de instalar Office 2016 en CLIENTE1, en el cuadro **Lo primero es lo primero**, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="35611-153">If you just installed Office 2016 on CLIENT1, in the **First things first** box, click **Accept**.</span></span>
    
4. <span data-ttu-id="35611-154">Haga clic en **Documento en blanco**. </span><span class="sxs-lookup"><span data-stu-id="35611-154">Click **Blank document**.</span></span> 
    
    <span data-ttu-id="35611-155">Tenga en cuenta la sección **Protección** de la cinta de opciones en la pestaña **Inicio** y la fila de clasificaciones de documentos.</span><span class="sxs-lookup"><span data-stu-id="35611-155">Note the **Protection** section of the ribbon on the **Home** tab and the row of document classifications.</span></span>
    
5. <span data-ttu-id="35611-156">En el documento en blanco, escriba algunas palabras.</span><span class="sxs-lookup"><span data-stu-id="35611-156">In the blank document, type some text.</span></span>
    
6. <span data-ttu-id="35611-157">Haga clic en **Archivo > Guardar**, escriba el nombre **BeforeAIP** y, después, haga clic en **Aceptar**. </span><span class="sxs-lookup"><span data-stu-id="35611-157">Click **File > Save**, type the name **BeforeAIP**, and then click **OK**.</span></span> 
    
7. <span data-ttu-id="35611-158">En la fila de clases de documentos, haga clic en la flecha hacia abajo para **Secreto** y, después, haga clic en **Toda la compañía**.</span><span class="sxs-lookup"><span data-stu-id="35611-158">In the row of document classes, click the down arrow for **Secret**, and then click **All Company**.</span></span>
    
8. <span data-ttu-id="35611-159">Haga clic en **Archivo > Guardar como**, escriba el nombre **AfterAIP** y, después, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="35611-159">Click **File > Save As**, type the name **AfterAIP**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="35611-160">Haga clic en **Explorador de archivos** en la barra de tareas y, después, abra la carpeta **Documentos**.</span><span class="sxs-lookup"><span data-stu-id="35611-160">Click **File Explorer** in the taskbar, and then open the **Documents** folder.</span></span>
    
    <span data-ttu-id="35611-161">Tenga en cuenta los tamaños de archivo diferentes de los documentos **BeforeAIP** y **AfterAIP**.</span><span class="sxs-lookup"><span data-stu-id="35611-161">Note the different file sizes of the **BeforeAIP** and **AfterAIP** documents.</span></span> <span data-ttu-id="35611-162">El documento AfterAIP es más grande porque tiene la información de clasificación.</span><span class="sxs-lookup"><span data-stu-id="35611-162">The AfterAIP document is larger because it has the classification information.</span></span>
    
<span data-ttu-id="35611-163">Después, permita que todos los usuarios tengan acceso a la colección de sitios de soporte.</span><span class="sxs-lookup"><span data-stu-id="35611-163">Next, you allow everyone to access the Support site collection.</span></span>
  
1. <span data-ttu-id="35611-164">	En la pestaña *\*Página principal de Microsoft Office*\*, haga clic en *\*SharePoint*\*.</span><span class="sxs-lookup"><span data-stu-id="35611-164">On the **Microsoft Office Home** tab, click **SharePoint**.</span></span>
    
2. <span data-ttu-id="35611-165">Desde la pestaña **SharePoint**, haga clic en **Colección de sitios de soporte**.</span><span class="sxs-lookup"><span data-stu-id="35611-165">From the **SharePoint** tab, click **Support site collection**.</span></span>
    
3. <span data-ttu-id="35611-166">En la esquina superior derecha, haga clic en el icono **Configuración** y, después, en **Compartido con**.</span><span class="sxs-lookup"><span data-stu-id="35611-166">In the upper right, click the **Settings** icon, and then click **Shared with**.</span></span>
    
4. <span data-ttu-id="35611-167">En **compartir "colección de sitios de soporte"**, haga clic en **Opciones avanzadas**.</span><span class="sxs-lookup"><span data-stu-id="35611-167">In **Share 'Support site collection'**, click **Advanced**.</span></span>
    
5. <span data-ttu-id="35611-168">En la lista de grupos de SharePoint, haga clic en **Miembros de la colección de sitios de soporte**.</span><span class="sxs-lookup"><span data-stu-id="35611-168">In the list of SharePoint groups, click **Support site collection Members**.</span></span>
    
6. <span data-ttu-id="35611-169">En la página **Personas y grupos**, haga clic en **Nuevo**.</span><span class="sxs-lookup"><span data-stu-id="35611-169">On the **People and Groups** page, click **New**.</span></span>
    
7. <span data-ttu-id="35611-170">En **compartir "colección de sitios de soporte"**, escriba **todos**, haga clic en **todos excepto los usuarios externos**y, a continuación, haga clic en **compartir.**</span><span class="sxs-lookup"><span data-stu-id="35611-170">In **Share 'Support site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share.**</span></span>
    
8. <span data-ttu-id="35611-171">Cierre la pestaña **Personas y grupos**.</span><span class="sxs-lookup"><span data-stu-id="35611-171">Close the **People and Groups** tab.</span></span>
    
<span data-ttu-id="35611-172">Después, inicie sesión con su cuenta Usuario5 y cargue el documento protegido por AIP a la carpeta Documentos de la colección de sitios de soporte.</span><span class="sxs-lookup"><span data-stu-id="35611-172">Next, you sign in with your User5 account and upload the AIP-protected document to the Documents folder of the Support site collection.</span></span>
  
1. <span data-ttu-id="35611-173">En la pestaña **Página principal de Microsoft Office**, en la esquina superior derecha, haga clic en el icono de usuario y, después, en **Cerrar sesión**.</span><span class="sxs-lookup"><span data-stu-id="35611-173">On the **Microsoft Office Home** tab, in the upper right, click the user icon, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="35611-174">Vaya a [http://admin.microsoft.com](http://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="35611-174">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="35611-175">En la página **Office 365 de inicio de sesión** , haga clic en el nombre de cuenta usuario5 e inicie sesión.</span><span class="sxs-lookup"><span data-stu-id="35611-175">On the **Office 365 sign in** page, click the User5 account name and sign in.</span></span>
    
4. <span data-ttu-id="35611-176">En la pestaña **Página principal de Microsoft Office**, haga clic en **SharePoint > colección de sitios de soporte**.</span><span class="sxs-lookup"><span data-stu-id="35611-176">On the **Microsoft Office Home** tab, click **SharePoint > Support site collection**.</span></span>
    
5. <span data-ttu-id="35611-177">Haga clic en **Documentos**, en **Cargar**, en el documento **AfterAIP** y, después, haga clic en **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="35611-177">Click **Documents**, click **Upload**, click the **AfterAIP** document, and then click **Open**.</span></span>
    
    <span data-ttu-id="35611-178">Debe ver el documento AfterAIP.docx en la carpeta Documentos de la colección de sitios de soporte.</span><span class="sxs-lookup"><span data-stu-id="35611-178">You should see AfterAIP.docx in the Documents folder on the Support site collection.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="35611-179">Vea también</span><span class="sxs-lookup"><span data-stu-id="35611-179">See Also</span></span>

[<span data-ttu-id="35611-180">Guías del entorno de pruebas de adopción de la nube (TLG)</span><span class="sxs-lookup"><span data-stu-id="35611-180">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="35611-181">Entorno de desarrollo y pruebas de Office 365 y EMS</span><span class="sxs-lookup"><span data-stu-id="35611-181">Office 365 and EMS dev/test environment</span></span>](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)
  
[<span data-ttu-id="35611-182">Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="35611-182">Azure Information Protection</span></span>](https://www.microsoft.com/cloud-platform/azure-information-protection)


