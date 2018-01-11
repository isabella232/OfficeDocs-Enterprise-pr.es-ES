---
title: "Protección de archivos confidenciales en el entorno de desarrollo y pruebas de Office 365"
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
ms.assetid: 27ecff45-06a6-4629-bc45-9dab4eef3a21
description: "Resumen: Configurar y demostrar cómo Information Rights Management de Office 365 protege los archivos confidenciales, incluso cuando se registran en la colección de sitios de SharePoint Online incorrecta."
ms.openlocfilehash: eb456c86b118556abde6a887fe8b9ab68300740b
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2018
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a><span data-ttu-id="20a8c-103">Protección de archivos confidenciales en el entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="20a8c-103">Sensitive file protection in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="20a8c-104">**Resumen:** Configurar y demostrar cómo Information Rights Management de Office 365 protege los archivos confidenciales, incluso cuando se registran en la colección de sitios de SharePoint Online incorrecta.</span><span class="sxs-lookup"><span data-stu-id="20a8c-104">**Summary:** Configure and demonstrate how Office 365 Information Rights Management protects your sensitive files, even when they are posted to the wrong SharePoint Online site collection.</span></span>
  
<span data-ttu-id="20a8c-p101">Information Rights Management (IRM) en Office 365 es un conjunto de características para proteger los documentos que se descargan de listas y bibliotecas de SharePoint Online. Los archivos descargados se cifran y contienen los permisos para abrir, copiar, guardar e imprimir que refleja la biblioteca de SharePoint Online en la que se almacenan.</span><span class="sxs-lookup"><span data-stu-id="20a8c-p101">Information Rights Management (IRM) in Office 365 is a set of capabilities to protect documents that are downloaded from SharePoint Online libraries and lists. Downloaded files are encrypted and contain the open, copy, save, and print permissions that reflect the SharePoint Online library in which they were stored.</span></span>
  
<span data-ttu-id="20a8c-107">Con las instrucciones de este artículo, habilite y pruebe IRM en Office 365 para archivos que contienen posible información confidencial en su suscripción de prueba de Office 365.</span><span class="sxs-lookup"><span data-stu-id="20a8c-107">With the instructions in this article, you enable and test IRM in Office 365 for files containing possible sensitive information in your Office 365 trial subscription.</span></span>
  
> [!TIP]
> <span data-ttu-id="20a8c-108">Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual para todos los artículos de la pila de una guía de laboratorio de prueba de nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="20a8c-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="20a8c-109">Fase 1: Crear el entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="20a8c-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="20a8c-110">Si desea probar la protección de archivos confidenciales en una manera ligera con los requisitos mínimos, siga las instrucciones en las fases 2 y 3 del [entorno de desarrollo y prueba de Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="20a8c-110">If you just want to test sensitive file protection in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="20a8c-111">Si desea probar la protección de archivos confidenciales en una empresa simulada, siga las instrucciones de [sincronización de directorios para el entorno de desarrollo y prueba de Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="20a8c-111">If you want to test sensitive file protection in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="20a8c-p102">Probar la protección de archivos confidenciales no requiere el entorno de desarrollo y pruebas de una empresa simulada, que incluye una intranet simulada conectada a Internet y la sincronización de directorios para un bosque de Windows Server AD. Aquí se ofrece como opción para que pueda probar la protección de archivos confidenciales y experimentar con ella en un entorno que representa una organización típica.</span><span class="sxs-lookup"><span data-stu-id="20a8c-p102">Testing sensitive file protection does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test sensitive file protection and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a><span data-ttu-id="20a8c-114">Fase 2: Mostrar cómo los documentos de sitios protegidos mediante permisos pueden perderse</span><span class="sxs-lookup"><span data-stu-id="20a8c-114">Phase 2: Demonstrate how documents from permissions-protected sites can be leaked</span></span>

<span data-ttu-id="20a8c-115">En esta fase, muestra que un usuario puede descargar un documento de un sitio protegido mediante permisos y, después, cargarlo en un sitio que tenga permisos abiertos.</span><span class="sxs-lookup"><span data-stu-id="20a8c-115">In this phase, you demonstrate that someone can download a document from a permissions-protected site and then upload it to a site that has wide-open permissions.</span></span>
  
<span data-ttu-id="20a8c-116">En primer lugar, agregue tres cuentas de usuario nuevas que representen a ejecutivos y asígneles licencias de Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="20a8c-116">First, you add three new user accounts that represent executives and assign them Office 365 E5 licenses.</span></span>
  
<span data-ttu-id="20a8c-117">Siga las instrucciones de [conectarse a Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) para instalar los módulos de PowerShell (si es necesario) y conectarse a la nueva suscripción de Office 365 desde:</span><span class="sxs-lookup"><span data-stu-id="20a8c-117">Use the instructions in [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) to install the PowerShell modules (if needed) and connect to your new Office 365 subscription from:</span></span>
  
- <span data-ttu-id="20a8c-118">Su equipo (para el entorno de desarrollo y pruebas ligero de Office 365).</span><span class="sxs-lookup"><span data-stu-id="20a8c-118">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="20a8c-119">La máquina virtual CLIENT1 (para el entorno de desarrollo y pruebas de una empresa simulada de Office 365).</span><span class="sxs-lookup"><span data-stu-id="20a8c-119">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
<span data-ttu-id="20a8c-120">En el cuadro de diálogo **Solicitud de credencial de Windows PowerShell** , escriba el nombre de administrador global de Office 365 (ejemplo: jdoe@contosotoycompany.onmicrosoft.com) y la contraseña de su suscripción de prueba de Office 365.</span><span class="sxs-lookup"><span data-stu-id="20a8c-120">In the **Windows PowerShell Credential Request** dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password of your Office 365 trial subscription.</span></span>
  
<span data-ttu-id="20a8c-121">Rellene el nombre de su organización (ejemplo: contosotoycompany), el código de país de dos caracteres para su ubicación y, después, ejecute los siguientes comandos desde el símbolo del sistema de Módulo Windows Azure Active Directory para Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="20a8c-121">Fill in your organization name (example: contosotoycompany) and the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="20a8c-122">En la pantalla del comando **MsolUser de nuevo** , observe la contraseña generada para la cuenta de director general y grabarlo en un lugar seguro.</span><span class="sxs-lookup"><span data-stu-id="20a8c-122">From the display of the **New-MsolUser** command, note the generated password for the CEO account and record it in a safe location.</span></span>
  
<span data-ttu-id="20a8c-123">Ejecute los siguientes comandos desde el símbolo del sistema del Módulo de Windows Azure Active Directory para Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="20a8c-123">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="20a8c-124">En la pantalla del comando **MsolUser de nuevo** , anote la contraseña para la cuenta de director financiero generada y grabarlo en un lugar seguro.</span><span class="sxs-lookup"><span data-stu-id="20a8c-124">From the display of the **New-MsolUser** command, note the generated password for the CFO account and record it in a safe location.</span></span>
  
<span data-ttu-id="20a8c-125">Ejecute los siguientes comandos desde el símbolo del sistema del Módulo de Windows Azure Active Directory para Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="20a8c-125">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="20a8c-126">En la pantalla del comando **MsolUser de nuevo** , tenga en cuenta la contraseña generada para la cuenta de director de operaciones y grabarla en un lugar seguro.</span><span class="sxs-lookup"><span data-stu-id="20a8c-126">From the display of the **New-MsolUser** command, note the generated password for the COO account and record it in a safe location.</span></span>
  
<span data-ttu-id="20a8c-127">Después, cree un grupo privado de ejecutivos y agregue en él las nuevas cuentas de ejecutivo.</span><span class="sxs-lookup"><span data-stu-id="20a8c-127">Next, you create a private Executives group and add the new executive accounts to it.</span></span>
  
1. <span data-ttu-id="20a8c-128">En el explorador, visite el portal de Office en [http://portal.office.com](http://portal.office.com) e inicie sesión a su suscripción de prueba de Office 365 con su cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="20a8c-128">In your browser, go to the Office portal at [http://portal.office.com](http://portal.office.com) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
  - <span data-ttu-id="20a8c-129">Si usa el entorno de desarrollo y pruebas ligero de Office 365, abra una sesión privada con Internet Explorer o con su explorador e inicie sesión desde el equipo local.</span><span class="sxs-lookup"><span data-stu-id="20a8c-129">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer or your browser and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="20a8c-130">Si usa el entorno de desarrollo y pruebas de una empresa simulada de Office 365, use Azure Portal para conectarse a la máquina virtual CLIENTE1 e inicie sesión desde esta.</span><span class="sxs-lookup"><span data-stu-id="20a8c-130">If you are using the simulated enterprise Office 365 dev/test environment, use the Azure portal to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="20a8c-131">En la ficha **Página de inicio de Microsoft Office** , haga clic en **Admin > grupos > grupos de**y, a continuación, haga clic en **Agregar un grupo**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-131">On the **Microsoft Office Home** tab, click **Admin > Groups > Groups**, and then click **Add a group**.</span></span>
    
3. <span data-ttu-id="20a8c-132">En **Agregar un grupo**, seleccione **grupo de Office 365** para el tipo de grupo, escriba **ejecutivos** en **nombre** e **Identificador de grupo**, seleccione la opción de **privacidad** **privado** y, a continuación, haga clic en **Seleccionar propietario**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-132">In **Add a group**, select **Office 365 group** for the group type, type **Executives** in **Name** and **Group Id**, select **Private** for **Privacy**, and then click **Select Owner**.</span></span>
    
4. <span data-ttu-id="20a8c-133">En la lista, haga clic en el nombre de cuenta del administrador global.</span><span class="sxs-lookup"><span data-stu-id="20a8c-133">In the list, click your global administrator account name.</span></span>
    
5. <span data-ttu-id="20a8c-134">Haga clic en **Agregar**y, a continuación, haga clic en **Cerrar**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-134">Click **Add**, and then click **Close**.</span></span>
    
6. <span data-ttu-id="20a8c-135">En la lista grupos, haga clic en **ejecutivos**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-135">In the groups list, click **Executives**.</span></span>
    
7. <span data-ttu-id="20a8c-136">Haga clic en **Editar para miembros**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-136">Click **Edit for Members**.</span></span>
    
8. <span data-ttu-id="20a8c-p103">Haga clic en **Agregar miembros**. En la lista de miembros, seleccione las cuentas de usuario siguientes:</span><span class="sxs-lookup"><span data-stu-id="20a8c-p103">Click **Add members**. In the member list, select the following user accounts:</span></span>
    
  - <span data-ttu-id="20a8c-139">Director ejecutivo principal</span><span class="sxs-lookup"><span data-stu-id="20a8c-139">Chief Executive Officer</span></span>
    
  - <span data-ttu-id="20a8c-140">Director financiero</span><span class="sxs-lookup"><span data-stu-id="20a8c-140">Chief Financial Officer</span></span>
    
  - <span data-ttu-id="20a8c-141">Director de operaciones</span><span class="sxs-lookup"><span data-stu-id="20a8c-141">Chief Operations Officer</span></span>
    
9. <span data-ttu-id="20a8c-142">Haga clic en **Guardar**y, a continuación, haga clic en **Cerrar**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-142">Click **Save**, and then click **Close**.</span></span>
    
10. <span data-ttu-id="20a8c-143">Cierre la ficha de **Centro de administración de Office** .</span><span class="sxs-lookup"><span data-stu-id="20a8c-143">Close the **Office Admin center** tab.</span></span>
    
<span data-ttu-id="20a8c-144">Después, cree una colección de sitios de ejecutivos y permita que solo tengan acceso a ella los miembros del grupo Ejecutivos.</span><span class="sxs-lookup"><span data-stu-id="20a8c-144">Next, you create an Executives site collection and allow just the members of the Executives group to access it.</span></span>
  
1. <span data-ttu-id="20a8c-145">En la ficha **Página de inicio de Microsoft Office** , haga clic en el mosaico de **Admin** .</span><span class="sxs-lookup"><span data-stu-id="20a8c-145">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="20a8c-146">En la ficha del **Centro de administración de Office** , haga clic en **centros de Admin > SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-146">On the **Office Admin center** tab, click **Admin centers > SharePoint**.</span></span>
    
3. <span data-ttu-id="20a8c-147">En la ficha del **Centro de administración de SharePoint** , haga clic en **Nuevo > colección de sitios privado**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-147">On the **SharePoint admin center** tab, click **New > Private site collection**.</span></span>
    
4. <span data-ttu-id="20a8c-148">En el nuevo panel de colección de sitios, escriba **ejecutivos** en **título**, en el cuadro Dirección URL, los ejecutivos especificar el nombre de la cuenta de administrador global en **Administrador**y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-148">In the new site collection pane, type **Executives** in **Title**, executives in the URL box, specify the name of your global administrator account in **Administrator**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="20a8c-p104">Espere hasta que se ha creado la nueva colección de sitios. Cuando haya finalizado, copie la dirección URL de la nueva colección de sitios de ejecutivos y pegarla en una nueva ficha del explorador.</span><span class="sxs-lookup"><span data-stu-id="20a8c-p104">Wait until the new site collection has been created. When complete, copy the URL of the new Executives site collection and paste it into a new tab of your browser.</span></span>
    
6. <span data-ttu-id="20a8c-151">En la parte superior derecha de la colección de sitios de **ejecutivos** , haga clic en el icono de configuración y, a continuación, haga clic en **compartido con**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-151">In the upper right of the **Executives** site collection, click the settings icon, and then click **Shared with**.</span></span>
    
7. <span data-ttu-id="20a8c-152">En el **recurso compartido 'Ejecutivos'**, haga clic en **Avanzadas**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-152">In **Share 'Executives'**, click **Advanced**.</span></span>
    
8. <span data-ttu-id="20a8c-153">En la lista de grupos de SharePoint, haga clic en **Miembros de ejecutivos**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-153">In the list of SharePoint groups, click **Executives Members**.</span></span>
    
9. <span data-ttu-id="20a8c-154">En la página **personas y grupos** , haga clic en **nuevo**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-154">On the **People and Groups** page, click **New**.</span></span>
    
10. <span data-ttu-id="20a8c-155">En el **recurso compartido 'Ejecutivos'**, escriba **ejecutivos**, haga clic en el grupo de **ejecutivos** y, a continuación, haga clic en **Compartir**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-155">In **Share 'Executives'**, type **Executives**, click the **Executives** group, and then click **Share**.</span></span>
    
11. <span data-ttu-id="20a8c-156">Cierre la ficha **usuarios y grupos** .</span><span class="sxs-lookup"><span data-stu-id="20a8c-156">Close the **People and groups** tab.</span></span>
    
<span data-ttu-id="20a8c-157">Después, permita que todos los usuarios tengan acceso a la colección de sitios de ventas.</span><span class="sxs-lookup"><span data-stu-id="20a8c-157">Next, you allow everyone to access the Sales site collection.</span></span>
  
1. <span data-ttu-id="20a8c-158">Desde la ficha del **Centro de administración de SharePoint** , copie la dirección URL de la colección de sitios de ventas y pegarla en una nueva ficha del explorador..</span><span class="sxs-lookup"><span data-stu-id="20a8c-158">From the **SharePoint admin center** tab, copy the URL of the Sales site collection and paste it into a new tab of your browser..</span></span>
    
2. <span data-ttu-id="20a8c-159">En la parte superior derecha, haga clic en el icono de configuración y, a continuación, haga clic en **compartido con**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-159">In the upper right, click the settings icon, and then click **Shared with**.</span></span>
    
3. <span data-ttu-id="20a8c-160">En el **recurso compartido 'Colección de sitios de ventas'**, haga clic en **Avanzadas**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-160">In **Share 'Sales site collection'**, click **Advanced**.</span></span>
    
4. <span data-ttu-id="20a8c-161">En la lista de grupos de SharePoint, haga clic en **los miembros de la colección de sitios de ventas**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-161">In the list of SharePoint groups, click **Sales site collection Members**.</span></span>
    
5. <span data-ttu-id="20a8c-162">En la página **personas y grupos** , haga clic en **nuevo**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-162">On the **People and Groups** page, click **New**.</span></span>
    
6. <span data-ttu-id="20a8c-163">En el **recurso compartido 'Colección de sitios de ventas'**, escriba **todos**, haga clic en **todos excepto los usuarios externos**y, a continuación, haga clic en **Compartir**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-163">In **Share 'Sales site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share**.</span></span>
    
7. <span data-ttu-id="20a8c-164">Cierra las fichas de la **colección de sitios de ventas** y **SharePoint** .</span><span class="sxs-lookup"><span data-stu-id="20a8c-164">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="20a8c-165">Después, inicie sesión con una cuenta de ejecutivo y cree un documento en la colección de sitios de ejecutivos.</span><span class="sxs-lookup"><span data-stu-id="20a8c-165">Next, you sign in with an executive account and create a document in the Executives site collection.</span></span>
  
1. <span data-ttu-id="20a8c-166">En la ficha **Página de inicio de Microsoft Office** , haga clic en el icono de usuario en la parte superior derecha y, a continuación, haga clic en **Cerrar sesión**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-166">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="20a8c-167">Vaya a [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="20a8c-167">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="20a8c-168">En la página **Office 365 iniciar sesión en** , haga clic en **usar otra cuenta**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-168">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="20a8c-169">Escriba el nombre de la cuenta de **Director general** y su contraseña y, a continuación, haga clic en **iniciar sesión**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-169">Type the **CEO** account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="20a8c-170">En una nueva pestaña del explorador, escriba la dirección URL de la colección de sitios de ejecutivos ( **https://**\<nombre de la organización >**.sharepoint.com/sites/executives**).</span><span class="sxs-lookup"><span data-stu-id="20a8c-170">On a new tab of your browser, type the URL to the Executives site collection ( **https://**\<organization name>**.sharepoint.com/sites/executives**).</span></span>
    
6. <span data-ttu-id="20a8c-171">Haga clic en **documentos**, haga clic en **nuevo** y, a continuación, haga clic en **Documento de Word**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-171">Click **Documents**, click **New,** and then click **Word Document**.</span></span>
    
7. <span data-ttu-id="20a8c-172">Haga clic en la barra de título y escriba **SensitiveData-BeforeIRM**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-172">Click in the title bar and type **SensitiveData-BeforeIRM**.</span></span>
    
8. <span data-ttu-id="20a8c-173">Haga clic en el cuerpo del documento, escriba los **minutos desde la última reunión de la junta**y, a continuación, haga clic en **ejecutivos**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-173">Click in the document body and type **Minutes from the latest board meeting**, and then click **Executives**.</span></span>
    
     <span data-ttu-id="20a8c-174">Debería ver **BeforeIRM.docx de SensitiveData** en la carpeta **documentos** .</span><span class="sxs-lookup"><span data-stu-id="20a8c-174">You should see **SensitiveData-BeforeIRM.docx** in the **Documents** folder.</span></span>
    
<span data-ttu-id="20a8c-175">Después, descargue una copia local del documento SensitiveData-BeforeIRM.docx y, luego, publíquelo en la colección de sitios de ventas accidentalmente.</span><span class="sxs-lookup"><span data-stu-id="20a8c-175">Next, you download a local copy of the SensitiveData-BeforeIRM.docx document and then accidentally post it to the Sales site collection.</span></span>
  
1. <span data-ttu-id="20a8c-176">En el equipo local, cree una nueva carpeta (por ejemplo, C:\\TLGs\\SensitiveDataTestFiles).</span><span class="sxs-lookup"><span data-stu-id="20a8c-176">On your local computer, create a new folder (for example, C:\\TLGs\\SensitiveDataTestFiles).</span></span>
    
2. <span data-ttu-id="20a8c-177">En la ficha de **documentos** del explorador, seleccione el documento de **BeforeIRM.docx de SensitiveData** , haga clic en los puntos suspensivos y, a continuación, haga clic en **Descargar**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-177">On the **Documents** tab of your browser, select the **SensitiveData-BeforeIRM.docx** document, click the ellipses, and then click **Download**.</span></span>
    
3. <span data-ttu-id="20a8c-178">Guarde el documento **BeforeIRM.docx de SensitiveData** en la carpeta creada en el paso 1.</span><span class="sxs-lookup"><span data-stu-id="20a8c-178">Store the **SensitiveData-BeforeIRM.docx** document in the folder created in step 1.</span></span>
    
4. <span data-ttu-id="20a8c-179">En una nueva pestaña del explorador, escriba la dirección URL de la colección de sitios de ventas ( **https://**\<nombre de la organización >**.sharepoint.com/sites/sales**).</span><span class="sxs-lookup"><span data-stu-id="20a8c-179">On a new tab of your browser, type the URL to the Sales site collection ( **https://**\<organization name>**.sharepoint.com/sites/sales**).</span></span>
    
5. <span data-ttu-id="20a8c-180">Haga clic en la carpeta de **documentos** de la **colección de sitios de ventas**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-180">Click the **Documents** folder of the **Sales site collection**.</span></span>
    
6. <span data-ttu-id="20a8c-181">Haga clic en **cargar**y a continuación, especifique el documento **BeforeIRM.docx de SensitiveData** en la carpeta que creó en el paso 1 y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-181">Click **Upload**, and then specify **SensitiveData-BeforeIRM.docx** document in the folder created in step 1, and then click **OK**.</span></span>
    
7. <span data-ttu-id="20a8c-182">Compruebe que el documento **BeforeIRM.docx de SensitiveData** está en la carpeta **documentos** .</span><span class="sxs-lookup"><span data-stu-id="20a8c-182">Verify that the **SensitiveData-BeforeIRM.docx** document is in the **Documents** folder.</span></span>
    
8. <span data-ttu-id="20a8c-183">Cierra las fichas **ventas** y **SharePoint** .</span><span class="sxs-lookup"><span data-stu-id="20a8c-183">Close the **Sales** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="20a8c-184">Después, inicie sesión como Usuario5 y pruebe a abrir el documento SensitiveData-BeforeIRM.docx en la colección de sitios de ventas.</span><span class="sxs-lookup"><span data-stu-id="20a8c-184">Next, you sign in as User5 and try to open the SensitiveData-BeforeIRM.docx document in the Sales site collection.</span></span>
  
1. <span data-ttu-id="20a8c-185">En la ficha **Página de inicio de Microsoft Office** , haga clic en el icono de usuario en la parte superior derecha y, a continuación, haga clic en **Cerrar sesión**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-185">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="20a8c-186">Vaya a [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="20a8c-186">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="20a8c-187">En la página **Office 365 iniciar sesión en** , haga clic en **usar otra cuenta**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-187">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="20a8c-188">Escriba el nombre de la cuenta usuario5 y su contraseña y, a continuación, haga clic en **iniciar sesión**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-188">Type the User5 account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="20a8c-189">En una nueva pestaña del explorador, escriba la dirección URL de la colección de sitios de ventas.</span><span class="sxs-lookup"><span data-stu-id="20a8c-189">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
6. <span data-ttu-id="20a8c-190">En la carpeta de **documentos** de la **colección de sitios de ventas**, haga clic en el documento **BeforeIRM.docx de SensitiveData** .</span><span class="sxs-lookup"><span data-stu-id="20a8c-190">In the **Documents** folder of the **Sales site collection**, click the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
    <span data-ttu-id="20a8c-191">Debe ver su contenido.</span><span class="sxs-lookup"><span data-stu-id="20a8c-191">You should see its contents.</span></span>
    
7. <span data-ttu-id="20a8c-192">Cierra las fichas de **documentos** y **colección de sitios de ventas** .</span><span class="sxs-lookup"><span data-stu-id="20a8c-192">Close the **Documents** and **Sales site collection** tabs.</span></span>
    
<span data-ttu-id="20a8c-193">Al publicar accidentalmente el documento SensitiveData-BeforeIRM.docx en la colección de sitios de ventas, el CEO ha ignorado la seguridad de los permisos de la colección de sitios de ejecutivos.</span><span class="sxs-lookup"><span data-stu-id="20a8c-193">By accidentally posting the SensitiveData-BeforeIRM.docx document on the Sales site collection, the CEO bypassed the permissions security of the Executives site collection.</span></span>
  
<span data-ttu-id="20a8c-194">Para preparar Office 365 para las fases 3 y 4, habilite IRM para SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="20a8c-194">To prepare Office 365 for Phases 3 and 4, enable IRM for SharePoint Online.</span></span>
  
1. <span data-ttu-id="20a8c-195">En la ficha **Página de inicio de Microsoft Office** , haga clic en el icono de usuario en la parte superior derecha y, a continuación, haga clic en **Cerrar sesión**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-195">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="20a8c-196">Vaya a [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="20a8c-196">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="20a8c-197">En la página **Office 365 iniciar sesión en** , haga clic en el nombre de la cuenta de administrador global, escriba su contraseña y, a continuación, haga clic en **Inicio de sesión**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-197">On the **Office 365 sign in** page, click the global administrator account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="20a8c-198">En la ficha **Página de inicio de Microsoft Office** , haga clic en **Admin > centros de Admin > SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-198">On the **Microsoft Office Home** tab, click **Admin > Admin centers > SharePoint**.</span></span>
    
5. <span data-ttu-id="20a8c-199">En la ficha del **Centro de administración de SharePoint** , haga clic en **configuración**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-199">On the **SharePoint admin center** tab, click **Settings**.</span></span>
    
6. <span data-ttu-id="20a8c-200">En la página de **configuración** , en la sección de **Information Rights Management (IRM)** , seleccione **usar el servicio IRM especificado en la configuración**y, a continuación, seleccione **Actualizar configuración de IRM**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-200">On the **Settings** page, in the **Information Rights Management (IRM)** section, select **Use the IRM service specified in your configuration**, and then select **Refresh IRM Settings**.</span></span>
    
7. <span data-ttu-id="20a8c-201">Cierre la ficha de **Centro de administración de SharePoint** .</span><span class="sxs-lookup"><span data-stu-id="20a8c-201">Close the **SharePoint admin center** tab.</span></span>
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a><span data-ttu-id="20a8c-202">Fase 3: Usar SharePoint Information Rights Management con un grupo privado de Office 365</span><span class="sxs-lookup"><span data-stu-id="20a8c-202">Phase 3: Use SharePoint Information Rights Management with an Office 365 private group</span></span>

<span data-ttu-id="20a8c-203">En esta fase, usa SharePoint Information Rights Management con un grupo privado de Office 365 para proteger el acceso a un documento con información confidencial, incluso cuando se ha publicado en un sitio con permisos abiertos.</span><span class="sxs-lookup"><span data-stu-id="20a8c-203">In this phase, you use SharePoint Information Rights Management with an Office 365 private group to protect access to a document with sensitive information, even when it is posted on a site with open permissions.</span></span>
  
<span data-ttu-id="20a8c-204">Primero, habilite y configure IRM para la biblioteca de documentos de la colección de sitios de ejecutivos. </span><span class="sxs-lookup"><span data-stu-id="20a8c-204">First, you enable and configure IRM for the documents library of the Executives site collection.</span></span> 
  
1. <span data-ttu-id="20a8c-205">En una nueva pestaña del explorador, escriba la dirección URL de la colección de sitios de ejecutivos.</span><span class="sxs-lookup"><span data-stu-id="20a8c-205">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
2. <span data-ttu-id="20a8c-206">Haga clic en **documentos**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-206">Click **Documents**.</span></span>
    
3. <span data-ttu-id="20a8c-207">En la parte superior derecha, haga clic en el icono de configuración y, a continuación, haga clic en **configuración de la biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-207">In the upper-right, click the settings icon, and then click **Library settings**.</span></span>
    
4. <span data-ttu-id="20a8c-208">En la página de **configuración** , en **permisos y administración**, haga clic en **Information Rights Management**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-208">On the **Settings** page, under **Permissions and Management**, click **Information Rights Management**.</span></span>
    
5. <span data-ttu-id="20a8c-209">En la página **Configuración de Information Rights Management** :</span><span class="sxs-lookup"><span data-stu-id="20a8c-209">On the **Information Rights Management Settings** page:</span></span>
    
  - <span data-ttu-id="20a8c-210">Seleccione **restringir el acceso a los documentos de esta biblioteca al descargarlos**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-210">Select **Restrict permission to documents in this library on download**.</span></span>
    
  - <span data-ttu-id="20a8c-211">Para **crear un título de directiva de permisos**, escriba **ejecutivos**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-211">For **Create a permission policy title**, type **Executives**.</span></span>
    
  - <span data-ttu-id="20a8c-212">Para **Agregar una descripción de la directiva de permiso**, escriba **IRM para ejecutivos**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-212">For **Add a permission policy description**, type **IRM for executives**.</span></span>
    
6. <span data-ttu-id="20a8c-213">Haga clic en **Mostrar opciones**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-213">Click **Show Options**.</span></span>
    
7. <span data-ttu-id="20a8c-214">En **establecer la configuración de la biblioteca IRM adicionales**, seleccione **no permitir a los usuarios cargar documentos que no admitan IRM**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-214">Under **Set additional IRM library settings**, select **Do not allow users to upload documents that do not support IRM**.</span></span>
    
8. <span data-ttu-id="20a8c-215">En **Configurar derechos de acceso de documento**, seleccione **Permitir visores para imprimir** y **visores de permitir escribir en una copia del documento descargado**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-215">Under **Configure document access rights**, select **Allow viewers to print** and **Allow viewers to write on a copy of the downloaded document**.</span></span>
    
9. <span data-ttu-id="20a8c-216">En **Establecer grupo de protección y el intervalo de credenciales**, seleccione **Permitir protección de grupo** y para el **grupo predeterminado**, escriba **ejecutivos**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-216">Under **Set group protection and credentials interval**, select **Allow group protection** and for **Default group**, type **Executives**.</span></span>
    
10. <span data-ttu-id="20a8c-217">Haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-217">Click **OK**.</span></span>
    
<span data-ttu-id="20a8c-218">Después, actuando como el CEO, cargue un documento nuevo en la carpeta de documentos Ejecutivos, descárguelo y, después, cárguelo accidentalmente en la carpeta de documentos de ventas.</span><span class="sxs-lookup"><span data-stu-id="20a8c-218">Next, acting as the CEO, you upload a new document to the Executives document folder, download it, then accidentally upload it to the Sales document folder.</span></span>
  
1. <span data-ttu-id="20a8c-219">Abra la carpeta local donde se almacena el documento **BeforeIRM.docx de SensitiveData** .</span><span class="sxs-lookup"><span data-stu-id="20a8c-219">Open the local folder where you stored the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
2. <span data-ttu-id="20a8c-220">Haga clic en **BeforeIRM.docx de SensitiveData**y, a continuación, haga clic en **Copiar**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-220">Right-click **SensitiveData-BeforeIRM.docx**, and then click **Copy**.</span></span>
    
3. <span data-ttu-id="20a8c-221">Pulse el botón derecho dentro de la carpeta y, a continuación, haga clic en **Pegar**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-221">Right-click within the folder, and then click **Paste**.</span></span>
    
4. <span data-ttu-id="20a8c-222">Cambie el nombre del nuevo archivo **SensitiveData-BeforeIRM - Copy.docx** **SensitiveData AfterIRM.docx**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-222">Rename the new **SensitiveData-BeforeIRM - Copy.docx** file to **SensitiveData-AfterIRM.docx**.</span></span>
    
5. <span data-ttu-id="20a8c-223">Desde la ficha **Página de inicio de Microsoft Office** en el explorador, haga clic en el icono de usuario en la parte superior derecha y, a continuación, haga clic en **Cerrar sesión**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-223">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
6. <span data-ttu-id="20a8c-224">Vaya a [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="20a8c-224">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
7. <span data-ttu-id="20a8c-225">En la página **Office 365 iniciar sesión en** , haga clic en el nombre de la cuenta de director ejecutivo, escriba su contraseña y, a continuación, haga clic en **Inicio de sesión**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-225">On the **Office 365 sign in** page, click the CEO account name, type its password, and then click **Sign in**.</span></span>
    
8. <span data-ttu-id="20a8c-226">En una nueva pestaña del explorador, escriba la dirección URL de la colección de sitios de ejecutivos.</span><span class="sxs-lookup"><span data-stu-id="20a8c-226">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
9. <span data-ttu-id="20a8c-227">En la página de **los documentos** , haga clic en **cargar**, especificar el documento **AfterIRM.docx de SensitiveData** en la carpeta local y, a continuación, haga clic en **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-227">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
10. <span data-ttu-id="20a8c-228">Seleccione el nuevo documento de **AfterIRM.docx de SensitiveData** en la página de **los documentos** , haga clic en el botón de puntos suspensivos (...) en la barra de menús y, a continuación, haga clic en **Descargar**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-228">Select the new **SensitiveData-AfterIRM.docx** document in the **Documents** page, click the ellipsis (…) in the menu bar, and then click **Download**.</span></span>
    
11. <span data-ttu-id="20a8c-229">Cuando se le pida, guarde el documento **AfterIRM.docx de SensitiveData** en la carpeta local, sobrescribiendo la versión original.</span><span class="sxs-lookup"><span data-stu-id="20a8c-229">When prompted, save the **SensitiveData-AfterIRM.docx** document in your local folder, overwriting the original version.</span></span>
    
12. <span data-ttu-id="20a8c-230">Cierre la ficha de la página de **los documentos** .</span><span class="sxs-lookup"><span data-stu-id="20a8c-230">Close the tab for the **Documents** page.</span></span>
    
13. <span data-ttu-id="20a8c-231">En una nueva pestaña del explorador, escriba la dirección URL de la colección de sitios de ventas.</span><span class="sxs-lookup"><span data-stu-id="20a8c-231">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
14. <span data-ttu-id="20a8c-232">Haga clic en **documentos**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-232">Click **Documents**.</span></span>
    
15. <span data-ttu-id="20a8c-233">En la página de **los documentos** , haga clic en **cargar**, especificar el documento **AfterIRM.docx de SensitiveData** en la carpeta local y, a continuación, haga clic en **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-233">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
16. <span data-ttu-id="20a8c-234">Cierra las fichas de la **colección de sitios de ventas** y **SharePoint** .</span><span class="sxs-lookup"><span data-stu-id="20a8c-234">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="20a8c-235">Actúa como un usuario normal, a continuación, intenta tener acceso al documento de **AfterIRM.docx de SensitiveData** en la carpeta de documentos de ventas.</span><span class="sxs-lookup"><span data-stu-id="20a8c-235">Next, acting as a normal user, you try to access the **SensitiveData-AfterIRM.docx** document in the Sales document folder.</span></span>
  
1. <span data-ttu-id="20a8c-236">Desde la ficha **Página de inicio de Microsoft Office** en el explorador, haga clic en el icono de usuario en la parte superior derecha y, a continuación, haga clic en **Cerrar sesión**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-236">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="20a8c-237">Vaya a [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="20a8c-237">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="20a8c-238">En la página **Office 365 iniciar sesión en** , haga clic en el nombre de la cuenta usuario5, escriba su contraseña y, a continuación, haga clic en **Inicio de sesión**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-238">On the **Office 365 sign in** page, click the User5 account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="20a8c-239">En una nueva pestaña del explorador, escriba la dirección URL de la colección de sitios de ventas.</span><span class="sxs-lookup"><span data-stu-id="20a8c-239">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
5. <span data-ttu-id="20a8c-240">Haga clic en **documentos**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-240">Click **Documents**.</span></span>
    
6. <span data-ttu-id="20a8c-241">En la página **documentos** , abra el documento de **AfterIRM.docx de SensitiveData** .</span><span class="sxs-lookup"><span data-stu-id="20a8c-241">On the **Documents** page, open the **SensitiveData-AfterIRM.docx** document.</span></span>
    
    <span data-ttu-id="20a8c-242">Debe ver un mensaje que diga "Word Online no puede abrir este documento porque está protegido por Information Rights Management (IRM)". </span><span class="sxs-lookup"><span data-stu-id="20a8c-242">You should see a message that states "Sorry, Word Online can't open this document because it's protected by Information Rights Management (IRM)."</span></span> 
    
7. <span data-ttu-id="20a8c-p105">Haga clic en **Editar en Word**. Se le pedirá si desea abrir el archivo. Haga clic en **Sí**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-p105">Click **Edit in Word**. You are prompted if you want to open the file. Click **Yes**.</span></span>
    
8. <span data-ttu-id="20a8c-p106">Se le pedirá que el inicio de sesión. Escriba el nombre de la cuenta usuario5 y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-p106">You are prompted to sign-in. Type the account name of the User5 account, and then click **Next**.</span></span>
    
9. <span data-ttu-id="20a8c-p107">Se le pedirá que proporcione la contraseña. Escriba la contraseña de la cuenta usuario5 y, a continuación, haga clic en **iniciar sesión**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-p107">You are prompted to provide the password. Type the password for the User5 account and then click **Sign in**.</span></span> 
    
    <span data-ttu-id="20a8c-250">Debe ver un mensaje que diga: "No tiene las credenciales para abrir este documento".</span><span class="sxs-lookup"><span data-stu-id="20a8c-250">You should see the a message that states: "You do not have the credentials that allow you to open this document."</span></span>
    
10. <span data-ttu-id="20a8c-251">Haga clic en **No**.</span><span class="sxs-lookup"><span data-stu-id="20a8c-251">Click **No**.</span></span>
    
<span data-ttu-id="20a8c-p108">Otra forma de ver la protección de IRM es mirar los archivos de la carpeta local. El **AfterIRM.docx de SensitiveData** debe ser mucho mayor que el archivo **SensitiveData-BeforeIRM.docx** . Se cifra el archivo **SensitiveData-AfterIRM.docx** y ha agregado la información de la protección de IRM.</span><span class="sxs-lookup"><span data-stu-id="20a8c-p108">Another way to see the IRM protection is to look at the files in your local folder. The **SensitiveData-AfterIRM.docx** should be much larger than the **SensitiveData-BeforeIRM.docx** file. The **SensitiveData-AfterIRM.docx** file is encrypted and has the IRM protection information added to it.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="20a8c-255">Consulte también</span><span class="sxs-lookup"><span data-stu-id="20a8c-255">See Also</span></span>

[<span data-ttu-id="20a8c-256">Guías del laboratorio de pruebas de adopción de la nube (TLG)</span><span class="sxs-lookup"><span data-stu-id="20a8c-256">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="20a8c-257">Entorno de desarrollo y pruebas de la configuración básica</span><span class="sxs-lookup"><span data-stu-id="20a8c-257">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="20a8c-258">Entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="20a8c-258">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="20a8c-259">Adopción de la nube y soluciones híbridas</span><span class="sxs-lookup"><span data-stu-id="20a8c-259">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


