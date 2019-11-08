---
title: Protección de archivos confidenciales en el entorno de desarrollo y pruebas de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/01/2019
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
ms.assetid: 27ecff45-06a6-4629-bc45-9dab4eef3a21
description: 'Resumen: Configure y demuestre cómo Office 365 Information Rights Management protege los archivos confidenciales, incluso cuando se publican en la colección de sitios incorrecta de SharePoint Online.'
ms.openlocfilehash: 3fa771d63ca30fb53ac2c77466546cf3a2098deb
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031575"
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a><span data-ttu-id="a8ffd-103">Protección de archivos confidenciales en el entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="a8ffd-103">Sensitive file protection in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="a8ffd-104">**Resumen:** Configure y muestre cómo Office 365 Information Rights Management protege los archivos confidenciales, incluso cuando se publican en la colección de sitios incorrecta de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-104">**Summary:** Configure and demonstrate how Office 365 Information Rights Management protects your sensitive files, even when they are posted to the wrong SharePoint Online site collection.</span></span>
  
<span data-ttu-id="a8ffd-p101">Information Rights Management (IRM) en Office 365 es un conjunto de características para proteger los documentos que se descargan de listas y bibliotecas de SharePoint Online. Los archivos descargados se cifran y contienen los permisos para abrir, copiar, guardar e imprimir que refleja la biblioteca de SharePoint Online en la que se almacenan.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-p101">Information Rights Management (IRM) in Office 365 is a set of capabilities to protect documents that are downloaded from SharePoint Online libraries and lists. Downloaded files are encrypted and contain the open, copy, save, and print permissions that reflect the SharePoint Online library in which they were stored.</span></span>
  
<span data-ttu-id="a8ffd-107">Con las instrucciones de este artículo, habilite y pruebe IRM en Office 365 para archivos que contienen posible información confidencial en su suscripción de prueba de Office 365.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-107">With the instructions in this article, you enable and test IRM in Office 365 for files containing possible sensitive information in your Office 365 trial subscription.</span></span>
  
> [!TIP]
> <span data-ttu-id="a8ffd-108">Haga clic [aquí](https://aka.ms/catlgstack) para ver un mapa visual de todos los artículos en la pila de la Guía del laboratorio de pruebas de Office 365.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-108">Click [here](https://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="a8ffd-109">Fase 1: Crear el entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="a8ffd-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="a8ffd-110">Si solo quiere probar la protección de archivos confidenciales de forma ligera con los requisitos mínimos, siga las instrucciones indicadas en las fases 2 y 3 de [Office 365 dev/test environment](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="a8ffd-110">If you just want to test sensitive file protection in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="a8ffd-111">Si quiere probar la protección de archivos confidenciales en una empresa simulada, siga las instrucciones indicadas en [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="a8ffd-111">If you want to test sensitive file protection in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="a8ffd-112">La comprobación de la protección de archivos confidenciales no requiere el entorno de desarrollo y pruebas de una empresa simulada, que incluye una intranet simulada conectada a Internet y la sincronización de directorios para un bosque de servicios de dominio de Active Directory (AD DS).</span><span class="sxs-lookup"><span data-stu-id="a8ffd-112">Testing sensitive file protection does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Active Directory Domain Services (AD DS) forest.</span></span> <span data-ttu-id="a8ffd-113">Aquí se ofrece como opción para que pueda probar la protección de archivos confidenciales y experimentar con ella en un entorno que representa una organización típica.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-113">It is provided here as an option so that you can test sensitive file protection and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a><span data-ttu-id="a8ffd-114">Fase 2: Mostrar cómo los documentos de sitios protegidos mediante permisos pueden perderse</span><span class="sxs-lookup"><span data-stu-id="a8ffd-114">Phase 2: Demonstrate how documents from permissions-protected sites can be leaked</span></span>

<span data-ttu-id="a8ffd-115">En esta fase, muestra que un usuario puede descargar un documento de un sitio protegido mediante permisos y, después, cargarlo en un sitio que tenga permisos abiertos.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-115">In this phase, you demonstrate that someone can download a document from a permissions-protected site and then upload it to a site that has wide-open permissions.</span></span>
  
<span data-ttu-id="a8ffd-116">En primer lugar, agregue tres cuentas de usuario nuevas que representen a ejecutivos y asígneles licencias de Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-116">First, you add three new user accounts that represent executives and assign them Office 365 E5 licenses.</span></span>
  
<span data-ttu-id="a8ffd-117">Siga las instrucciones de [conectarse a office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) para instalar los módulos de PowerShell (si es necesario) y conectarse a la nueva suscripción de Office 365 desde:</span><span class="sxs-lookup"><span data-stu-id="a8ffd-117">Use the instructions in [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) to install the PowerShell modules (if needed) and connect to your new Office 365 subscription from:</span></span>
  
- <span data-ttu-id="a8ffd-118">Su equipo (para el entorno de desarrollo y pruebas ligero de Office 365).</span><span class="sxs-lookup"><span data-stu-id="a8ffd-118">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="a8ffd-119">La máquina virtual CLIENTE1 (para el entorno de desarrollo y pruebas de una empresa ficticia de Office 365).</span><span class="sxs-lookup"><span data-stu-id="a8ffd-119">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
<span data-ttu-id="a8ffd-120">En el cuadro de diálogo **Solicitud de credenciales para Windows PowerShell**, escriba el nombre de administrador global de Office 365 (ejemplo: jdoe@contosotoycompany.onmicrosoft.com) y la contraseña de su suscripción de prueba de Office 365.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-120">In the **Windows PowerShell Credential Request** dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password of your Office 365 trial subscription.</span></span>
  
<span data-ttu-id="a8ffd-121">Rellene el nombre de su organización (ejemplo: contosotoycompany), el código de país de dos caracteres para su ubicación y, después, ejecute los siguientes comandos desde el símbolo del sistema de Módulo Windows Azure Active Directory para Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="a8ffd-121">Fill in your organization name (example: contosotoycompany) and the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="a8ffd-122">Desde la pantalla del comando **New-MsolUser**, anote la contraseña generada para la cuenta de CEO y guárdela en un lugar seguro.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-122">From the display of the **New-MsolUser** command, note the generated password for the CEO account and record it in a safe location.</span></span>
  
<span data-ttu-id="a8ffd-123">Ejecute los siguientes comandos desde el símbolo del sistema del Módulo de Windows Azure Active Directory para Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="a8ffd-123">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="a8ffd-124">Desde la pantalla del comando **New-MsolUser**, anote la contraseña generada para la cuenta de CFO y guárdela en un lugar seguro.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-124">From the display of the **New-MsolUser** command, note the generated password for the CFO account and record it in a safe location.</span></span>
  
<span data-ttu-id="a8ffd-125">Ejecute los siguientes comandos desde el símbolo del sistema del Módulo de Windows Azure Active Directory para Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="a8ffd-125">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="a8ffd-126">Desde la pantalla del comando **New-MsolUser**, anote la contraseña generada para la cuenta de COO y guárdela en un lugar seguro.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-126">From the display of the **New-MsolUser** command, note the generated password for the COO account and record it in a safe location.</span></span>
  
<span data-ttu-id="a8ffd-127">Después, cree un grupo privado de ejecutivos y agregue en él las nuevas cuentas de ejecutivo.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-127">Next, you create a private Executives group and add the new executive accounts to it.</span></span>
  
1. <span data-ttu-id="a8ffd-128">En el explorador, vaya al portal de Office en [https://admin.microsoft.com](https://admin.microsoft.com) e inicie sesión en su suscripción de prueba de Office 365 con su cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-128">In your browser, go to the Office portal at [https://admin.microsoft.com](https://admin.microsoft.com) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
  - <span data-ttu-id="a8ffd-129">Si usa el entorno de desarrollo y pruebas ligero de Office 365, abra una sesión privada con Internet Explorer o con su explorador e inicie sesión desde el equipo local.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-129">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer or your browser and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="a8ffd-130">Si usa el entorno de desarrollo y pruebas de una empresa simulada de Office 365, use Azure Portal para conectarse a la máquina virtual CLIENTE1 e inicie sesión desde esta.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-130">If you are using the simulated enterprise Office 365 dev/test environment, use the Azure portal to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="a8ffd-131">En la pestaña **Página principal de Microsoft Office**, haga clic en **Administración > Grupos > Grupos** y, después, haga clic en **Agregar un grupo**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-131">On the **Microsoft Office Home** tab, click **Admin > Groups > Groups**, and then click **Add a group**.</span></span>
    
3. <span data-ttu-id="a8ffd-132">En **Agregar un grupo**, seleccione **Grupo de Office 365** para el tipo de grupo, escriba **Ejecutivos** en **Nombre** e **Id. de grupo**, seleccione **Privada** para **Privacidad** y, después, haga clic en **Seleccionar propietario**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-132">In **Add a group**, select **Office 365 group** for the group type, type **Executives** in **Name** and **Group Id**, select **Private** for **Privacy**, and then click **Select Owner**.</span></span>
    
4. <span data-ttu-id="a8ffd-133">En la lista, haga clic en el nombre de cuenta del administrador global.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-133">In the list, click your global administrator account name.</span></span>
    
5. <span data-ttu-id="a8ffd-134">Haga clic en **Agregar** y, después, en **Cerrar**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-134">Click **Add**, and then click **Close**.</span></span>
    
6. <span data-ttu-id="a8ffd-135">En la lista de grupos, haga clic en **Ejecutivos**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-135">In the groups list, click **Executives**.</span></span>
    
7. <span data-ttu-id="a8ffd-136">Haga clic en **Edición de miembros**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-136">Click **Edit for Members**.</span></span>
    
8. <span data-ttu-id="a8ffd-p103">Haga clic en **Agregar miembros**. En la lista de miembros, seleccione las siguientes cuentas de usuario:</span><span class="sxs-lookup"><span data-stu-id="a8ffd-p103">Click **Add members**. In the member list, select the following user accounts:</span></span>
    
  - <span data-ttu-id="a8ffd-139">Director ejecutivo principal</span><span class="sxs-lookup"><span data-stu-id="a8ffd-139">Chief Executive Officer</span></span>
    
  - <span data-ttu-id="a8ffd-140">Director financiero</span><span class="sxs-lookup"><span data-stu-id="a8ffd-140">Chief Financial Officer</span></span>
    
  - <span data-ttu-id="a8ffd-141">Director de operaciones</span><span class="sxs-lookup"><span data-stu-id="a8ffd-141">Chief Operations Officer</span></span>
    
9. <span data-ttu-id="a8ffd-142">Haga clic en **Guardar** y, después, en **Cerrar**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-142">Click **Save**, and then click **Close**.</span></span>
    
10. <span data-ttu-id="a8ffd-143">Cierre la pestaña **Centro de administración de Office**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-143">Close the **Office Admin center** tab.</span></span>
    
<span data-ttu-id="a8ffd-144">Después, cree una colección de sitios de ejecutivos y permita que solo tengan acceso a ella los miembros del grupo Ejecutivos.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-144">Next, you create an Executives site collection and allow just the members of the Executives group to access it.</span></span>
  
1. <span data-ttu-id="a8ffd-145">En la pestaña **Página principal de Microsoft Office**, haga clic en el icono de **Administración**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-145">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="a8ffd-146">En la pestaña **centro de administración de Office** , haga clic en centros de **Administración > SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-146">On the **Office Admin center** tab, click **Admin centers > SharePoint**.</span></span>
    
3. <span data-ttu-id="a8ffd-147">En la pestaña **centro de administración de SharePoint** , haga clic en **nueva > colección de sitios privados**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-147">On the **SharePoint admin center** tab, click **New > Private site collection**.</span></span>
    
4. <span data-ttu-id="a8ffd-148">En el panel nueva colección de sitios, escriba **ejecutivos** en **título**, ejecutivos en el cuadro Dirección URL, especifique el nombre de la cuenta de administrador global en **Administrador**y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-148">In the new site collection pane, type **Executives** in **Title**, executives in the URL box, specify the name of your global administrator account in **Administrator**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="a8ffd-149">Espere hasta que se haya creado la nueva colección de sitios.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-149">Wait until the new site collection has been created.</span></span> <span data-ttu-id="a8ffd-150">Cuando haya finalizado, copie la dirección URL de la nueva colección de sitios de ejecutivos y péguela en una nueva pestaña del explorador.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-150">When complete, copy the URL of the new Executives site collection and paste it into a new tab of your browser.</span></span>
    
6. <span data-ttu-id="a8ffd-151">En la esquina superior derecha de la colección de sitios **Ejecutivos**, haga clic en el icono Configuración y, después, en **Compartido con**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-151">In the upper right of the **Executives** site collection, click the settings icon, and then click **Shared with**.</span></span>
    
7. <span data-ttu-id="a8ffd-152">En **compartir "ejecutivos"**, haga clic en **Opciones avanzadas**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-152">In **Share 'Executives'**, click **Advanced**.</span></span>
    
8. <span data-ttu-id="a8ffd-153">En la lista de grupos de SharePoint, haga clic en **Miembros ejecutivos**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-153">In the list of SharePoint groups, click **Executives Members**.</span></span>
    
9. <span data-ttu-id="a8ffd-154">En la página **Personas y grupos**, haga clic en **Nuevo**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-154">On the **People and Groups** page, click **New**.</span></span>
    
10. <span data-ttu-id="a8ffd-155">En **compartir "ejecutivos"**, escriba **ejecutivos**, haga clic en el grupo **ejecutivos** y, a continuación, haga clic en **compartir**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-155">In **Share 'Executives'**, type **Executives**, click the **Executives** group, and then click **Share**.</span></span>
    
11. <span data-ttu-id="a8ffd-156">Cierre la pestaña **personas y grupos** .</span><span class="sxs-lookup"><span data-stu-id="a8ffd-156">Close the **People and groups** tab.</span></span>
    
<span data-ttu-id="a8ffd-157">Después, permita que todos los usuarios tengan acceso a la colección de sitios de ventas.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-157">Next, you allow everyone to access the Sales site collection.</span></span>
  
1. <span data-ttu-id="a8ffd-158">En la pestaña **centro de administración de SharePoint** , copie la dirección URL de la colección de sitios de ventas y péguela en una nueva pestaña del explorador..</span><span class="sxs-lookup"><span data-stu-id="a8ffd-158">From the **SharePoint admin center** tab, copy the URL of the Sales site collection and paste it into a new tab of your browser..</span></span>
    
2. <span data-ttu-id="a8ffd-159">En la esquina superior derecha, haga clic en el icono Configuración y, después, en **Compartido con**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-159">In the upper right, click the settings icon, and then click **Shared with**.</span></span>
    
3. <span data-ttu-id="a8ffd-160">En **compartir "colección de sitios de ventas"**, haga clic en **Opciones avanzadas**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-160">In **Share 'Sales site collection'**, click **Advanced**.</span></span>
    
4. <span data-ttu-id="a8ffd-161">En la lista de grupos de SharePoint, haga clic en **Miembros de la colección de sitios de ventas**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-161">In the list of SharePoint groups, click **Sales site collection Members**.</span></span>
    
5. <span data-ttu-id="a8ffd-162">En la página **Personas y grupos**, haga clic en **Nuevo**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-162">On the **People and Groups** page, click **New**.</span></span>
    
6. <span data-ttu-id="a8ffd-163">En **compartir "colección de sitios de ventas"**, escriba **todos**, haga clic en **todos excepto los usuarios externos**y, después, haga clic en **compartir**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-163">In **Share 'Sales site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share**.</span></span>
    
7. <span data-ttu-id="a8ffd-164">Cierre las pestañas **Colección de sitios de ventas** y **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-164">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="a8ffd-165">Después, inicie sesión con una cuenta de ejecutivo y cree un documento en la colección de sitios de ejecutivos.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-165">Next, you sign in with an executive account and create a document in the Executives site collection.</span></span>
  
1. <span data-ttu-id="a8ffd-166">En la pestaña **Página principal de Microsoft Office**, haga clic en el icono de usuario en la esquina superior derecha y, después, en **Cerrar sesión**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-166">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="a8ffd-167">Vaya a [https://admin.microsoft.com](https://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="a8ffd-167">Go to [https://admin.microsoft.com](https://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="a8ffd-168">En la página **Inicio de sesión en Office 365**, haga clic en **Usar otra cuenta**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-168">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="a8ffd-169">Escriba el nombre de cuenta **CEO** y su contraseña y, luego, haga clic en **Iniciar sesión**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-169">Type the **CEO** account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="a8ffd-170">En una pestaña nueva del explorador, escriba la dirección URL de la colección de sitios de ejecutivos (nombre de la organización de **https://**\<>**. SharePoint.com/sites/Executives**).</span><span class="sxs-lookup"><span data-stu-id="a8ffd-170">On a new tab of your browser, type the URL to the Executives site collection ( **https://**\<organization name>**.sharepoint.com/sites/executives**).</span></span>
    
6. <span data-ttu-id="a8ffd-171">Haga clic en **documentos**, en **nuevo** y, a continuación, en **documento de Word**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-171">Click **Documents**, click **New,** and then click **Word Document**.</span></span>
    
7. <span data-ttu-id="a8ffd-172">Haga clic en la barra de título y escriba **SensitiveData-BeforeIRM**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-172">Click in the title bar and type **SensitiveData-BeforeIRM**.</span></span>
    
8. <span data-ttu-id="a8ffd-173">Haga clic en el cuerpo del documento, escriba **Minutos desde la última reunión del consejo de dirección** y, después, haga clic en **Ejecutivos**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-173">Click in the document body and type **Minutes from the latest board meeting**, and then click **Executives**.</span></span>
    
     <span data-ttu-id="a8ffd-174"> Debe ver **SensitiveData-BeforeIRM.docx** en la carpeta **Documentos**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-174">You should see **SensitiveData-BeforeIRM.docx** in the **Documents** folder.</span></span>
    
<span data-ttu-id="a8ffd-175">Después, descargue una copia local del documento SensitiveData-BeforeIRM.docx y, luego, publíquelo en la colección de sitios de ventas accidentalmente.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-175">Next, you download a local copy of the SensitiveData-BeforeIRM.docx document and then accidentally post it to the Sales site collection.</span></span>
  
1. <span data-ttu-id="a8ffd-176">En el equipo local, cree una carpeta nueva (por ejemplo, C:\\TLG\\SensitiveDataTestFiles).</span><span class="sxs-lookup"><span data-stu-id="a8ffd-176">On your local computer, create a new folder (for example, C:\\TLGs\\SensitiveDataTestFiles).</span></span>
    
2. <span data-ttu-id="a8ffd-177">En la pestaña **Documentos** de su explorador, seleccione el documento **SensitiveData-BeforeIRM.docx**, haga clic en los puntos suspensivos y, después, en **Descargar**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-177">On the **Documents** tab of your browser, select the **SensitiveData-BeforeIRM.docx** document, click the ellipses, and then click **Download**.</span></span>
    
3. <span data-ttu-id="a8ffd-178">Almacene el documento **SensitiveData-BeforeIRM.docx** en la carpeta que se ha creado en el paso 1.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-178">Store the **SensitiveData-BeforeIRM.docx** document in the folder created in step 1.</span></span>
    
4. <span data-ttu-id="a8ffd-179">En una pestaña nueva del explorador, escriba la dirección URL de la colección de sitios de ventas ( **https://**\<Organization Name>**. SharePoint.com/sites/sales**).</span><span class="sxs-lookup"><span data-stu-id="a8ffd-179">On a new tab of your browser, type the URL to the Sales site collection ( **https://**\<organization name>**.sharepoint.com/sites/sales**).</span></span>
    
5. <span data-ttu-id="a8ffd-180">Haga clic en la carpeta **Documentos** de la **Colección de sitios de ventas**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-180">Click the **Documents** folder of the **Sales site collection**.</span></span>
    
6. <span data-ttu-id="a8ffd-181">Haga clic en **Cargar**, especifique el documento **SensitiveData-BeforeIRM.docx** en la carpeta que se ha creado en el paso 1 y, después, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-181">Click **Upload**, and then specify **SensitiveData-BeforeIRM.docx** document in the folder created in step 1, and then click **OK**.</span></span>
    
7. <span data-ttu-id="a8ffd-182">Compruebe que el documento **SensitiveData-BeforeIRM.docx** se encuentra en la carpeta **Documentos**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-182">Verify that the **SensitiveData-BeforeIRM.docx** document is in the **Documents** folder.</span></span>
    
8. <span data-ttu-id="a8ffd-183">Cierre las pestañas **Ventas** y **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-183">Close the **Sales** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="a8ffd-184">Después, inicie sesión como Usuario5 y pruebe a abrir el documento SensitiveData-BeforeIRM.docx en la colección de sitios de ventas.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-184">Next, you sign in as User5 and try to open the SensitiveData-BeforeIRM.docx document in the Sales site collection.</span></span>
  
1. <span data-ttu-id="a8ffd-185">En la pestaña **Página principal de Microsoft Office**, haga clic en el icono de usuario en la esquina superior derecha y, después, en **Cerrar sesión**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-185">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="a8ffd-186">Vaya a [https://admin.microsoft.com](https://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="a8ffd-186">Go to [https://admin.microsoft.com](https://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="a8ffd-187">En la página **Inicio de sesión en Office 365**, haga clic en **Usar otra cuenta**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-187">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="a8ffd-188">Escriba el nombre de cuenta del Usuario5 y su contraseña y, después, haga clic en **Iniciar sesión**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-188">Type the User5 account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="a8ffd-189">En una pestaña nueva del explorador, escriba la dirección URL de la colección de sitios de ventas.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-189">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
6. <span data-ttu-id="a8ffd-190">En la carpeta **Documentos** de la **Colección de sitios de ventas**, haga clic en el documento **SensitiveData-BeforeIRM.docx**. </span><span class="sxs-lookup"><span data-stu-id="a8ffd-190">In the **Documents** folder of the **Sales site collection**, click the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
    <span data-ttu-id="a8ffd-191">Debe ver su contenido.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-191">You should see its contents.</span></span>
    
7. <span data-ttu-id="a8ffd-192">Cierre las pestañas **Documentos** y **Colección de sitios de ventas**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-192">Close the **Documents** and **Sales site collection** tabs.</span></span>
    
<span data-ttu-id="a8ffd-193">Al publicar accidentalmente el documento SensitiveData-BeforeIRM.docx en la colección de sitios de ventas, el CEO ha ignorado la seguridad de los permisos de la colección de sitios de ejecutivos.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-193">By accidentally posting the SensitiveData-BeforeIRM.docx document on the Sales site collection, the CEO bypassed the permissions security of the Executives site collection.</span></span>
  
<span data-ttu-id="a8ffd-194">Para preparar Office 365 para las fases 3 y 4, habilite IRM para SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-194">To prepare Office 365 for Phases 3 and 4, enable IRM for SharePoint Online.</span></span>
  
1. <span data-ttu-id="a8ffd-195">En la pestaña **Página principal de Microsoft Office**, haga clic en el icono de usuario en la esquina superior derecha y, después, en **Cerrar sesión**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-195">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="a8ffd-196">Vaya a [https://admin.microsoft.com](https://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="a8ffd-196">Go to [https://admin.microsoft.com](https://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="a8ffd-197">En la página **Inicio de sesión en Office 365**, haga clic en el nombre de cuenta del administrador global, escriba su contraseña y, después, haga clic en **Iniciar sesión**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-197">On the **Office 365 sign in** page, click the global administrator account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="a8ffd-198">En la pestaña **Página principal de Microsoft Office**, haga clic en **Administración > Centros de administración > SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-198">On the **Microsoft Office Home** tab, click **Admin > Admin centers > SharePoint**.</span></span>
    
5. <span data-ttu-id="a8ffd-199">En la pestaña **Centro de administración de SharePoint**, haga clic en **Configuración**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-199">On the **SharePoint admin center** tab, click **Settings**.</span></span>
    
6. <span data-ttu-id="a8ffd-200">En la página, en la sección **Information Rights Management (IRM)** , seleccione **usar el servicio de IRM especificado en su configuración**y, después, seleccione **Actualizar configuración de IRM**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-200">On the page, in the **Information Rights Management (IRM)** section, select **Use the IRM service specified in your configuration**, and then select **Refresh IRM Settings**.</span></span>
    
7. <span data-ttu-id="a8ffd-201">Cierre la pestaña **Centro de administración de SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-201">Close the **SharePoint admin center** tab.</span></span>
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a><span data-ttu-id="a8ffd-202">Fase 3: Usar SharePoint Information Rights Management con un grupo privado de Office 365</span><span class="sxs-lookup"><span data-stu-id="a8ffd-202">Phase 3: Use SharePoint Information Rights Management with an Office 365 private group</span></span>

<span data-ttu-id="a8ffd-203">En esta fase, usa SharePoint Information Rights Management con un grupo privado de Office 365 para proteger el acceso a un documento con información confidencial, incluso cuando se ha publicado en un sitio con permisos abiertos.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-203">In this phase, you use SharePoint Information Rights Management with an Office 365 private group to protect access to a document with sensitive information, even when it is posted on a site with open permissions.</span></span>
  
<span data-ttu-id="a8ffd-204">Primero, habilite y configure IRM para la biblioteca de documentos de la colección de sitios de ejecutivos. </span><span class="sxs-lookup"><span data-stu-id="a8ffd-204">First, you enable and configure IRM for the documents library of the Executives site collection.</span></span> 
  
1. <span data-ttu-id="a8ffd-205">En una pestaña nueva del explorador, escriba la dirección URL de la colección de sitios de ejecutivos.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-205">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
2. <span data-ttu-id="a8ffd-206">Haga clic en **Documentos**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-206">Click **Documents**.</span></span>
    
3. <span data-ttu-id="a8ffd-207">En la esquina superior derecha, haga clic en el icono de configuración y, después, en **Configuración de la biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-207">In the upper-right, click the settings icon, and then click **Library settings**.</span></span>
    
4. <span data-ttu-id="a8ffd-208">En la página **Configuración**, en **Permisos y administración**, haga clic en **Information Rights Management**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-208">On the **Settings** page, under **Permissions and Management**, click **Information Rights Management**.</span></span>
    
5. <span data-ttu-id="a8ffd-209">En la página de **Configuración de Information Rights Management**:</span><span class="sxs-lookup"><span data-stu-id="a8ffd-209">On the **Information Rights Management Settings** page:</span></span>
    
  - <span data-ttu-id="a8ffd-210">Seleccione **Restringir permisos de acceso a los documentos de esta biblioteca al descargarlos**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-210">Select **Restrict permission to documents in this library on download**.</span></span>
    
  - <span data-ttu-id="a8ffd-211">En **Crear un título de directiva de permisos**, escriba **Ejecutivos**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-211">For **Create a permission policy title**, type **Executives**.</span></span>
    
  - <span data-ttu-id="a8ffd-212">En **Agregar una descripción de la directiva de permisos**, escriba **IRM para ejecutivos**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-212">For **Add a permission policy description**, type **IRM for executives**.</span></span>
    
6. <span data-ttu-id="a8ffd-213">Haga clic en **Mostrar opciones**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-213">Click **Show Options**.</span></span>
    
7. <span data-ttu-id="a8ffd-214">En **Definir configuración adicional de la biblioteca de IRM**, seleccione **No permitir a los usuarios cargar documentos que no admitan IRM**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-214">Under **Set additional IRM library settings**, select **Do not allow users to upload documents that do not support IRM**.</span></span>
    
8. <span data-ttu-id="a8ffd-215">En **Configurar derechos de acceso de documentos**, seleccione **Permitir que los lectores impriman** y **Permitir a los lectores escribir en una copia del documento descargado**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-215">Under **Configure document access rights**, select **Allow viewers to print** and **Allow viewers to write on a copy of the downloaded document**.</span></span>
    
9. <span data-ttu-id="a8ffd-216">En **establecer intervalo de credenciales y protección de grupo**, seleccione **permitir la protección de grupos. Grupo predeterminado**y, a continuación, escriba **ejecutivos**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-216">Under **Set group protection and credentials interval**, select **Allow group protection. Default group**, and then type **Executives**.</span></span>
    
10. <span data-ttu-id="a8ffd-217">Haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-217">Click **OK**.</span></span>
    
<span data-ttu-id="a8ffd-218">Después, actuando como el CEO, cargue un documento nuevo en la carpeta de documentos Ejecutivos, descárguelo y, después, cárguelo accidentalmente en la carpeta de documentos de ventas.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-218">Next, acting as the CEO, you upload a new document to the Executives document folder, download it, then accidentally upload it to the Sales document folder.</span></span>
  
1. <span data-ttu-id="a8ffd-219">Abra la carpeta local donde ha almacenado el documento **SensitiveData-BeforeIRM.docx**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-219">Open the local folder where you stored the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
2. <span data-ttu-id="a8ffd-220">	Haga clic con el botón derecho en *\*SensitiveData-BeforeIRM.docx** y, después, haga clic en *\*Copiar*\*.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-220">Right-click **SensitiveData-BeforeIRM.docx**, and then click **Copy**.</span></span>
    
3. <span data-ttu-id="a8ffd-221">Haga clic con el botón derecho dentro de la carpeta y, después, en **Pegar**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-221">Right-click within the folder, and then click **Paste**.</span></span>
    
4. <span data-ttu-id="a8ffd-222">Cambie el nombre del nuevo archivo **SensitiveData-BeforeIRM-Copy. docx** a **SensitiveData-AfterIRM. docx**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-222">Rename the new **SensitiveData-BeforeIRM - Copy.docx** file to **SensitiveData-AfterIRM.docx**.</span></span>
    
5. <span data-ttu-id="a8ffd-223">Desde la pestaña **Página principal de Microsoft Office** de su explorador, haga clic en el icono de usuario en la esquina superior derecha y, después, en **Cerrar sesión**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-223">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
6. <span data-ttu-id="a8ffd-224">Vaya a [https://admin.microsoft.com](https://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="a8ffd-224">Go to [https://admin.microsoft.com](https://admin.microsoft.com).</span></span>
    
7. <span data-ttu-id="a8ffd-225">En la página **Inicio de sesión en Office 365**, haga clic en el nombre de cuenta del CEO, escriba su contraseña y, después, haga clic en **Iniciar sesión**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-225">On the **Office 365 sign in** page, click the CEO account name, type its password, and then click **Sign in**.</span></span>
    
8. <span data-ttu-id="a8ffd-226">En una pestaña nueva del explorador, escriba la dirección URL de la colección de sitios de ejecutivos.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-226">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
9. <span data-ttu-id="a8ffd-227">En la página **Documentos**, haga clic en **Cargar**, especifique el documento **SensitiveData-AfterIRM.docx** de su carpeta local y, después, haga clic en **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-227">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
10. <span data-ttu-id="a8ffd-228">Seleccione el nuevo documento **SensitiveData-AfterIRM.docx** en la página **Documentos**, haga clic en los puntos suspensivos (...) de la barra de menús y, después, haga clic en **Descargar**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-228">Select the new **SensitiveData-AfterIRM.docx** document in the **Documents** page, click the ellipsis (…) in the menu bar, and then click **Download**.</span></span>
    
11. <span data-ttu-id="a8ffd-229">Cuando se le solicite, guarde el documento **SensitiveData-AfterIRM.docx** en su carpeta local, sobrescribiendo la versión original.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-229">When prompted, save the **SensitiveData-AfterIRM.docx** document in your local folder, overwriting the original version.</span></span>
    
12. <span data-ttu-id="a8ffd-230">Cierre la pestaña de la página **Documentos**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-230">Close the tab for the **Documents** page.</span></span>
    
13. <span data-ttu-id="a8ffd-231">En una pestaña nueva del explorador, escriba la dirección URL de la colección de sitios de ventas.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-231">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
14. <span data-ttu-id="a8ffd-232">Haga clic en **Documentos**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-232">Click **Documents**.</span></span>
    
15. <span data-ttu-id="a8ffd-233">En la página **Documentos**, haga clic en **Cargar**, especifique el documento **SensitiveData-AfterIRM.docx** de su carpeta local y, después, haga clic en **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-233">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
16. <span data-ttu-id="a8ffd-234">Cierre las pestañas **Colección de sitios de ventas** y **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-234">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="a8ffd-235">Después, actuando como un usuario normal, intente acceder al documento **SensitiveData-AfterIRM.docx** de la carpeta de documentos de ventas.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-235">Next, acting as a normal user, you try to access the **SensitiveData-AfterIRM.docx** document in the Sales document folder.</span></span>
  
1. <span data-ttu-id="a8ffd-236">Desde la pestaña **Página principal de Microsoft Office** de su explorador, haga clic en el icono de usuario en la esquina superior derecha y, después, en **Cerrar sesión**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-236">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="a8ffd-237">Vaya a [https://admin.microsoft.com](https://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="a8ffd-237">Go to [https://admin.microsoft.com](https://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="a8ffd-238">En la página **Office 365 de inicio de sesión** , haga clic en el nombre de cuenta usuario5, escriba su contraseña y, a continuación, haga clic en **iniciar sesión**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-238">On the **Office 365 sign in** page, click the User5 account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="a8ffd-239">En una pestaña nueva del explorador, escriba la dirección URL de la colección de sitios de ventas.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-239">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
5. <span data-ttu-id="a8ffd-240">Haga clic en **Documentos**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-240">Click **Documents**.</span></span>
    
6. <span data-ttu-id="a8ffd-241">En la página **Documentos**, abra el documento **SensitiveData-AfterIRM.docx**. </span><span class="sxs-lookup"><span data-stu-id="a8ffd-241">On the **Documents** page, open the **SensitiveData-AfterIRM.docx** document.</span></span>
    
    <span data-ttu-id="a8ffd-242">Debe ver un mensaje que indica "lo sentimos, Word no puede abrir este documento porque está protegido por Information Rights Management (IRM)."</span><span class="sxs-lookup"><span data-stu-id="a8ffd-242">You should see a message that states, "Sorry, Word can't open this document because it's protected by Information Rights Management (IRM)."</span></span> 
    
7. <span data-ttu-id="a8ffd-p105">Haga clic en **Editar en Word**. Se le solicitará si quiere abrir el archivo. Haga clic en **Sí**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-p105">Click **Edit in Word**. You are prompted if you want to open the file. Click **Yes**.</span></span>
    
8. <span data-ttu-id="a8ffd-p106">Se le solicitará que inicie sesión. Escriba el nombre de cuenta de la cuenta del Usuario5 y, después, haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-p106">You are prompted to sign-in. Type the account name of the User5 account, and then click **Next**.</span></span>
    
9. <span data-ttu-id="a8ffd-p107">Se le solicitará que proporcione la contraseña. Escriba la contraseña de la cuenta del Usuario5 y, después, haga clic en **Iniciar sesión**. </span><span class="sxs-lookup"><span data-stu-id="a8ffd-p107">You are prompted to provide the password. Type the password for the User5 account and then click **Sign in**.</span></span> 
    
    <span data-ttu-id="a8ffd-250">Debe ver un mensaje que diga: "No tiene las credenciales para abrir este documento".</span><span class="sxs-lookup"><span data-stu-id="a8ffd-250">You should see the a message that states: "You do not have the credentials that allow you to open this document."</span></span>
    
10. <span data-ttu-id="a8ffd-251">Haga clic en **No**.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-251">Click **No**.</span></span>
    
<span data-ttu-id="a8ffd-p108">Otra manera de ver la protección de IRM es mirar los archivos de su carpeta local. El documento **SensitiveData-AfterIRM.docx** debe ser mucho más grande que el archivo **SensitiveData-BeforeIRM.docx**. El archivo **SensitiveData-AfterIRM.docx** está cifrado y se ha agregado información de protección de IRM en él.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-p108">Another way to see the IRM protection is to look at the files in your local folder. The **SensitiveData-AfterIRM.docx** should be much larger than the **SensitiveData-BeforeIRM.docx** file. The **SensitiveData-AfterIRM.docx** file is encrypted and has the IRM protection information added to it.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a8ffd-255">Vea también</span><span class="sxs-lookup"><span data-stu-id="a8ffd-255">See Also</span></span>

[<span data-ttu-id="a8ffd-256">Guías del laboratorio de pruebas de adopción de la nube (TLG)</span><span class="sxs-lookup"><span data-stu-id="a8ffd-256">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="a8ffd-257">Entorno de desarrollo y pruebas de la configuración básica</span><span class="sxs-lookup"><span data-stu-id="a8ffd-257">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="a8ffd-258">Entorno de desarrollo y prueba de Office 365</span><span class="sxs-lookup"><span data-stu-id="a8ffd-258">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="a8ffd-259">Adopción de la nube y soluciones híbridas</span><span class="sxs-lookup"><span data-stu-id="a8ffd-259">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


