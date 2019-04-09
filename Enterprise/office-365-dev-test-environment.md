---
title: Entorno de desarrollo y pruebas de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/02/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 4f6035b8-2da3-4cf9-9657-5284d6364f7a
description: 'Resumen: use esta Guías del entorno de pruebas para crear una suscripción de prueba de Office 365 para evaluación, pruebas o desarrollo.'
ms.openlocfilehash: a49ba10ab9ddded36f21ca9cc92f0482cbe7a4fb
ms.sourcegitcommit: 201d3338d8bbc6da9389e62e2add8a17384fab4d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "31038040"
---
# <a name="office-365-devtest-environment"></a><span data-ttu-id="fcf08-103">Entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="fcf08-103">Office 365 dev/test environment</span></span>

 <span data-ttu-id="fcf08-104">**Resumen:** use esta Guías del entorno de pruebas para crear una suscripción de prueba de Office 365 para evaluación, pruebas o desarrollo.</span><span class="sxs-lookup"><span data-stu-id="fcf08-104">**Summary:** Use this Test Lab Guide to create an Office 365 trial subscription for evaluation or dev/test.</span></span>
  
<span data-ttu-id="fcf08-p101">Puede usar una suscripción de prueba de Office 365 y crear un entorno de desarrollo y pruebas de Office 365 para las aplicaciones o para demostrar las características y funcionalidades de Office 365. Existen dos versiones:</span><span class="sxs-lookup"><span data-stu-id="fcf08-p101">You can use an Office 365 trial subscription and create an Office 365 dev/test environment for applications or to demonstrate features and capabilities of Office 365. There are two versions:</span></span>
  
- <span data-ttu-id="fcf08-107">El entorno de desarrollo y pruebas ligero de Office 365 consiste en una suscripción de prueba de Office 365 a la que puede tener acceso desde su equipo principal.</span><span class="sxs-lookup"><span data-stu-id="fcf08-107">The lightweight Office 365 dev/test environment consists of an Office 365 trial subscription that you access from your main computer.</span></span>
    
    <span data-ttu-id="fcf08-p102">Use este entorno cuando quiera demostrar rápidamente una característica. Para el entorno de desarrollo y pruebas ligero de Office 365, complete solo las fases 2 y 3 de este artículo.</span><span class="sxs-lookup"><span data-stu-id="fcf08-p102">Use this environment when you want to quickly demonstrate a feature. For the lightweight Office 365 dev/test environment, complete only phases 2 and 3 of this article.</span></span>
    
- <span data-ttu-id="fcf08-p103">El entorno de desarrollo y pruebas de una empresa simulada de Office 365 consiste en una suscripción de prueba a Office 365 y una intranet simplificada de una organización conectada a Internet, que se hospeda en los servicios de infraestructura de Microsoft Azure. Puede crear esta configuración completamente en la nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="fcf08-p103">The simulated enterprise Office 365 dev/test environment consists of an Office 365 trial subscription and a simplified organization intranet connected to the Internet, which is hosted in Microsoft Azure infrastructure services. You can build this configuration completely in the Microsoft cloud.</span></span>
    
    <span data-ttu-id="fcf08-p104">Use este entorno cuando quiera demostrar una característica o una aplicación en un entorno que parece una red típica de la organización conectada a Internet, o para las características que requieran este tipo de entorno. Para el entorno de desarrollo y pruebas de una empresa simulada de Office 365, complete las fases 1, 2 y 3 de este artículo.</span><span class="sxs-lookup"><span data-stu-id="fcf08-p104">Use this environment when you want to demonstrate a feature or an app in an environment that resembles a typical organization network connected to the Internet, or for features that require this type of environment. For the simulated enterprise Office 365 dev/test environment, complete phases 1, 2, and 3 of this article.</span></span>
    
> [!NOTE]
> <span data-ttu-id="fcf08-p105">Es posible que quiera imprimir este artículo para anotar los valores específicos que necesite para usar este entorno durante los 30 días de la suscripción de prueba a Office 365. Puede extender fácilmente la suscripción de prueba otros 30 días. Para un entorno de pruebas y desarrollo permanente, cree una nueva suscripción de pago con un número reducido de licencias.</span><span class="sxs-lookup"><span data-stu-id="fcf08-p105">You might want to print this article to record the specific values that you will need for this environment over the 30 days of the Office 365 trial subscription. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
![Guías del entorno de pruebas en Microsoft Cloud](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="fcf08-118">Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual de todos los artículos en la pila de la Guía del entorno de pruebas de One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="fcf08-118">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-the-base-configuration-in-azure"></a><span data-ttu-id="fcf08-119">Fase 1: Crear la configuración básica de Azure</span><span class="sxs-lookup"><span data-stu-id="fcf08-119">Phase 1: Create the base configuration in Azure</span></span>

<span data-ttu-id="fcf08-120">Siga las instrucciones que se indican en [Configuración básica del entorno de desarrollo y pruebas](base-configuration-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="fcf08-120">Follow the instructions in [Base Configuration dev/test environment](base-configuration-dev-test-environment.md).</span></span>
  
<span data-ttu-id="fcf08-p106">Necesitará una suscripción de Azure. Para esta configuración, puede usar una [prueba gratuita de Azure](https://azure.microsoft.com/pricing/free-trial/). Si tiene una suscripción de MSDN o Visual Studio, vea [Crédito mensual de Azure para suscriptores de Visual Studio](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span><span class="sxs-lookup"><span data-stu-id="fcf08-p106">You will need an Azure subscription. You can use the [Azure Free Trial](https://azure.microsoft.com/pricing/free-trial/) for this configuration. If you have an MSDN or Visual Studio subscription, see [Monthly Azure credit for Visual Studio subscribers](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span></span>
  
<span data-ttu-id="fcf08-124">Esta es la configuración resultante.</span><span class="sxs-lookup"><span data-stu-id="fcf08-124">Here is the resulting configuration.</span></span>
  
![Configuración básica del entorno de desarrollo y pruebas en Azure](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)


  
<span data-ttu-id="fcf08-126">Esta configuración básica se compone de las máquinas virtuales DC1, APP1 y CLIENTE1 en una subred de una red virtual de Azure.</span><span class="sxs-lookup"><span data-stu-id="fcf08-126">This configuration consists of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
  
## <a name="phase-2-create-an-office-365-trial-subscription"></a><span data-ttu-id="fcf08-127">Fase 2: Crear una suscripción de prueba a Office 365</span><span class="sxs-lookup"><span data-stu-id="fcf08-127">Phase 2: Create an Office 365 trial subscription</span></span>

<span data-ttu-id="fcf08-128">Para iniciar la suscripción de prueba a Office 365 E5, primero necesita el nombre de una compañía ficticia y una nueva cuenta Microsoft.</span><span class="sxs-lookup"><span data-stu-id="fcf08-128">To start your Office 365 E5 trial subscription, you first need a fictitious company name and a new Microsoft account.</span></span>
  
1. <span data-ttu-id="fcf08-p107">Le recomendamos que use una variante del nombre de la compañía Contoso para el nombre de su compañía, que es una compañía ficticia usada en contenido de ejemplo de Microsoft, pero no es imprescindible. Anote aquí el nombre de la compañía ficticia: ![](./media/Common-Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="fcf08-p107">We recommend that you use a variant of the company name Contoso for your company name, which is a fictitious company used in Microsoft sample content, but it isn't required. Record your fictitious company name here: ![](./media/Common-Images/TableLine.png)</span></span>
    
2. <span data-ttu-id="fcf08-p108">Para registrarse para obtener una nueva cuenta Microsoft, vaya a [https://outlook.com](https://outlook.com) y cree una cuenta con una nueva cuenta y una dirección de correo electrónico. Usará esta cuenta para suscribirse a Office 365.</span><span class="sxs-lookup"><span data-stu-id="fcf08-p108">To sign up for a new Microsoft account, go to [https://outlook.com](https://outlook.com) and create an account with a new email account and address. You will use this account to sign up for Office 365.</span></span>
    
  - <span data-ttu-id="fcf08-133">Anote aquí el nombre y los apellidos de la nueva cuenta: ![](./media/Common-Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="fcf08-133">Record the first and last name of your new account here: ![](./media/Common-Images/TableLine.png)</span></span>
    
  - <span data-ttu-id="fcf08-134">Anote aquí la dirección de la nueva cuenta de correo electrónico: ![](./media/Common-Images/TableLine.png)@outlook.com</span><span class="sxs-lookup"><span data-stu-id="fcf08-134">Record the new email account address here: ![](./media/Common-Images/TableLine.png)@outlook.com</span></span>
    
### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a><span data-ttu-id="fcf08-135">Registrarse para una suscripción de prueba a Office 365 E5</span><span class="sxs-lookup"><span data-stu-id="fcf08-135">Sign up for an Office 365 E5 trial subscription</span></span>

1. <span data-ttu-id="fcf08-136">Para el entorno de desarrollo y pruebas ligero de Office 365, abra un explorador de Internet en el equipo y vaya a [https://aka.ms/e5trial](https://aka.ms/e5trial).</span><span class="sxs-lookup"><span data-stu-id="fcf08-136">For the lightweight Office 365 dev/test environment, open the Internet browser on your computer and go to [https://aka.ms/e5trial](https://aka.ms/e5trial).</span></span> 
    
    <span data-ttu-id="fcf08-137">Para el entorno de desarrollo y pruebas de Office 365 de la empresa ficticia, conéctese a CLIENTE1 con la cuenta CORP\Usuario1 desde Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="fcf08-137">For the simulated enterprise Office 365 dev/test environment, connect to CLIENT1 with the CORP\User1 account from the Azure portal.</span></span>

    <span data-ttu-id="fcf08-138">En la pantalla Inicio, ejecute Microsoft Edge y vaya a [https://aka.ms/e5trial](https://aka.ms/e5trial).</span><span class="sxs-lookup"><span data-stu-id="fcf08-138">From the Start screen, run Microsoft Edge and go to [https://aka.ms/e5trial](https://aka.ms/e5trial).</span></span>
    
2. <span data-ttu-id="fcf08-139">En la página **Bienvenido. Permítanos conocerle**, especifique:</span><span class="sxs-lookup"><span data-stu-id="fcf08-139">On the **Welcome, let's get to know you** page, specify:</span></span>
    
  - <span data-ttu-id="fcf08-140">Su ubicación física</span><span class="sxs-lookup"><span data-stu-id="fcf08-140">Your physical location</span></span>
    
  - <span data-ttu-id="fcf08-141">El nombre y apellidos de la nueva cuenta de Microsoft</span><span class="sxs-lookup"><span data-stu-id="fcf08-141">The first and last name of your new Microsoft account</span></span>
    
  - <span data-ttu-id="fcf08-142">La dirección de la nueva cuenta de correo</span><span class="sxs-lookup"><span data-stu-id="fcf08-142">Your new email account address</span></span>
    
  - <span data-ttu-id="fcf08-143">El número de teléfono del trabajo</span><span class="sxs-lookup"><span data-stu-id="fcf08-143">A business phone number</span></span>
    
  - <span data-ttu-id="fcf08-144">El nombre de la compañía ficticia</span><span class="sxs-lookup"><span data-stu-id="fcf08-144">Your fictional company name</span></span>
    
  - <span data-ttu-id="fcf08-145">El tamaño de la organización (250 a 999 personas)</span><span class="sxs-lookup"><span data-stu-id="fcf08-145">An organization size of 250-999 people</span></span>
    
3. <span data-ttu-id="fcf08-146">Haga clic en **Un solo paso más**.</span><span class="sxs-lookup"><span data-stu-id="fcf08-146">Click **Just one more step**.</span></span>
    
4. <span data-ttu-id="fcf08-147">En la página **Crear su id. de usuario**, escriba un nombre de usuario basado en la nueva dirección de correo, la empresa ficticia después del signo @ (quite todos los espacios en el nombre) y una contraseña (dos veces) para esta nueva cuenta de Office 365. </span><span class="sxs-lookup"><span data-stu-id="fcf08-147">On the **Create your user ID** page, type a user name based on your new email address, your fictional company after the @ sign (remove all spaces in the name), then a password (twice) for this new Office 365 account.</span></span>
    
    <span data-ttu-id="fcf08-148">Anote en un lugar seguro la contraseña que escriba.</span><span class="sxs-lookup"><span data-stu-id="fcf08-148">Record the password that you typed in a secure location.</span></span>
    
    <span data-ttu-id="fcf08-149">Anote aquí el nombre de la compañía ficticia, que se denominará **nombre de la organización**: ![](./media/Common-Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="fcf08-149">Record your fictional company name, to be referred to as the **organization name**, here: ![](./media/Common-Images/TableLine.png)</span></span>
    
5. <span data-ttu-id="fcf08-150">Haga clic en **Crear mi cuenta**.</span><span class="sxs-lookup"><span data-stu-id="fcf08-150">Click **Create my account**.</span></span>
    
6. <span data-ttu-id="fcf08-p109">En la página **Demuestre. Que. No. Es. Un. Robot.**, escriba el número de teléfono de su teléfono compatible con texto y, después, haga clic en **Enviarme un mensaje**.</span><span class="sxs-lookup"><span data-stu-id="fcf08-p109">On the **Prove. You're. Not. A. Robot.** page, type the phone number of your text-capable phone, and then click **Text me**.</span></span>
    
7. <span data-ttu-id="fcf08-153">Escriba el código de verificación del mensaje de texto recibido y, después, haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="fcf08-153">Type the verification code from the received text message, and then click **Next**.</span></span>
    
8. <span data-ttu-id="fcf08-154">Anote aquí la URL de la página de inicio de sesión (seleccionar y copiar): ![](./media/Common-Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="fcf08-154">Record the sign-in page URL here (select and copy): ![](./media/Common-Images/TableLine.png)</span></span>
    
9. <span data-ttu-id="fcf08-155">Anote aquí el identificador de usuario (seleccionar y copiar): ![](./media/Common-Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="fcf08-155">Record the user ID here (select and copy): ![](./media/Common-Images/TableLine.png).onmicrosoft.com</span></span>
    
    <span data-ttu-id="fcf08-156">Este valor se denominará **nombre de administrador global de Office 365**.</span><span class="sxs-lookup"><span data-stu-id="fcf08-156">This value will be referred to as the **Office 365 global administrator name**.</span></span>
    
10. <span data-ttu-id="fcf08-157">Cuando vea **Ya está listo**, haga clic.</span><span class="sxs-lookup"><span data-stu-id="fcf08-157">When you see **You're ready to go**, click it.</span></span>
    
11. <span data-ttu-id="fcf08-158">En la página siguiente, espere hasta que Office 365 complete la configuración y estén disponibles todos los iconos.</span><span class="sxs-lookup"><span data-stu-id="fcf08-158">On the next page, wait until Office 365 completes setting up and all the tiles are available.</span></span>
    
<span data-ttu-id="fcf08-159">Verá la página principal del portal de Office 365, desde donde puede obtener acceso a servicios de Office Online y al Centro de administración de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="fcf08-159">You should see main Office 365 portal page from which you can access Office Online services and the Microsoft 365 Admin center.</span></span>
  
<span data-ttu-id="fcf08-160">Para el entorno de desarrollo y pruebas de una empresa ficticia de Office 365, aquí se muestra la configuración resultante.</span><span class="sxs-lookup"><span data-stu-id="fcf08-160">For the simulated enterprise Office 365 dev/test environment, here is your resulting configuration.</span></span>
  
![El entorno de desarrollo y pruebas de Office 365](media/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
<span data-ttu-id="fcf08-162">Esta configuración se compone de:</span><span class="sxs-lookup"><span data-stu-id="fcf08-162">This configuration consists of:</span></span> 
  
- <span data-ttu-id="fcf08-163">Las máquinas virtuales DC1, APP1 y CLIENTE1 en una subred de una red virtual de Azure.</span><span class="sxs-lookup"><span data-stu-id="fcf08-163">The DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
    
- <span data-ttu-id="fcf08-164">Una suscripción de prueba a Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="fcf08-164">An Office 365 E5 Trial Subscription.</span></span>
    
## <a name="phase-3-configure-your-office-365-trial-subscription"></a><span data-ttu-id="fcf08-165">Fase 3: Configurar la suscripción de prueba de Office 365</span><span class="sxs-lookup"><span data-stu-id="fcf08-165">Phase 3: Configure your Office 365 trial subscription</span></span>

<span data-ttu-id="fcf08-166">En esta fase, se configura la suscripción a Office 365 con usuarios adicionales y se les asignan licencias de Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="fcf08-166">In this phase, you configure your Office 365 subscription with additional users and assign them Office 365 E5 licenses.</span></span>
  
<span data-ttu-id="fcf08-167">Siga las instrucciones que se indican en [Conectarse a PowerShell de Office 365](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-azure-active-directory-powershell-for-graph-module) para conectarse a su suscripción de Office 365 con el módulo Azure Active Directory PowerShell para Graph desde:</span><span class="sxs-lookup"><span data-stu-id="fcf08-167">Use the instructions in [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-azure-active-directory-powershell-for-graph-module) to connect to your Office 365 subscription with the Azure Active Directory PowerShell for Graph module from:</span></span>
  
- <span data-ttu-id="fcf08-168">Su equipo (para el entorno de desarrollo y pruebas ligero de Office 365).</span><span class="sxs-lookup"><span data-stu-id="fcf08-168">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="fcf08-169">La máquina virtual CLIENTE1 (para el entorno de desarrollo y pruebas de una empresa ficticia de Office 365).</span><span class="sxs-lookup"><span data-stu-id="fcf08-169">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
 <span data-ttu-id="fcf08-170">En el cuadro de diálogo Solicitud de credenciales para Windows PowerShell, escriba el nombre de administrador global de Office 365 (por ejemplo, svalladares@contosotoycompany.onmicrosoft.com) y la contraseña.</span><span class="sxs-lookup"><span data-stu-id="fcf08-170">In the Windows PowerShell Credential Request dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password.</span></span>
  
<span data-ttu-id="fcf08-171">Rellene el nombre de la organización (ejemplo: contosotoycompany), el código de país de dos caracteres para su ubicación, la contraseña de cuenta común y, después, ejecute los comandos siguientes desde el símbolo del sistema de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fcf08-171">Fill in your organization name (example: contosotoycompany), the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>

```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$commonPW="<common user account password>"
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPW

$userUPN= "user2@" + $orgName + ".onmicrosoft.com"
New-AzureADUser -DisplayName "User 2" -GivenName User -SurName 2 -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user2"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign

$userUPN= "user3@" + $orgName + ".onmicrosoft.com"
New-AzureADUser -DisplayName "User 3" -GivenName User -SurName 3 -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user3"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign

$userUPN= "user4@" + $orgName + ".onmicrosoft.com"
New-AzureADUser -DisplayName "User 4" -GivenName User -SurName 4 -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user4"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

<!--
> [!TIP]
> Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34) to get a text file that has all the PowerShell commands in this article.
-->

  
## <a name="phase-4-create-three-new-sharepoint-online-team-sites-optional"></a><span data-ttu-id="fcf08-172">Fase 4: Crear tres sitios de grupo de SharePoint Online (opcional)</span><span class="sxs-lookup"><span data-stu-id="fcf08-172">Phase 4: Create three new SharePoint Online team sites (optional)</span></span>

<span data-ttu-id="fcf08-173">En esta fase, configurará un conjunto de sitios de equipo de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="fcf08-173">In this phase, you configure a set of SharePoint Online team sites.</span></span>
  
1. <span data-ttu-id="fcf08-174">Instale el [Shell de administración de SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=255251) (la versión x64).</span><span class="sxs-lookup"><span data-stu-id="fcf08-174">Install the [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251) (the x64 version).</span></span>
    
2. <span data-ttu-id="fcf08-175">Haga clic en **Inicio**, escriba **sharepoint** y después haga clic en **Shell de administración de SharePoint Online**.</span><span class="sxs-lookup"><span data-stu-id="fcf08-175">Click **Start**, type **sharepoint**, and then click **SharePoint Online Management Shell**.</span></span>
    
3. <span data-ttu-id="fcf08-176">Rellene el nombre de su organización (ejemplo: contosotoycompany) y después ejecute los comandos siguientes desde el símbolo del sistema del Shell de administración de SharePoint Online para conectar con el servicio de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="fcf08-176">Fill in your organization name (example: contosotoycompany), and then run the following commands from the SharePoint Online Management Shell prompt to connect to the SharePoint Online service</span></span>
```
$orgName="<organization name>"
$spURL="https://" + $orgName + "-admin.sharepoint.com"
Connect-SPOService -Url $spURL
```

4. <span data-ttu-id="fcf08-177">En el cuadro de diálogo **Shell de administración de Microsoft SharePoint Online**, escriba el nombre del administrador global de Office 365 (por ejemplo, svalladares@contosotoycompany.onmicrosoft.com) y la contraseña y, después, haga clic en **Iniciar sesión**.</span><span class="sxs-lookup"><span data-stu-id="fcf08-177">In the **Microsoft SharePoint Online Management Shell** dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="fcf08-178">Para crear tres sitios de grupo (Ventas, Producción y Soporte técnico), rellene el nombre de administrador global de Office 365 y, después, ejecute los comandos siguientes desde el símbolo del sistema del Shell de administración de SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="fcf08-178">To create three new team sites (Sales, Production, and Support), fill in the Office 365 global administrator name, and then run the following commands from the SharePoint Online Management Shell prompt:</span></span>
    
  ```
  $owner = "<global administrator account name>"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/sales"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Sales site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/production"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Production site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/support"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Support site collection" -Template "STS#0"
  ```

6. <span data-ttu-id="fcf08-179">Ejecute este comando para mostrar una lista de las direcciones URL de estos sitios nuevos:</span><span class="sxs-lookup"><span data-stu-id="fcf08-179">Run this command to list the URLs of these new sites:</span></span>
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

7. <span data-ttu-id="fcf08-180">En Internet Explorer, escriba la dirección URL del sitio de Producción para ver el sitio de grupo predeterminado de SharePoint Online para el departamento de Producción.</span><span class="sxs-lookup"><span data-stu-id="fcf08-180">In Internet Explorer, enter the URL of the Production site to see the default SharePoint Online team site for the Production department.</span></span>
    
## <a name="record-values-for-future-reference"></a><span data-ttu-id="fcf08-181">Anote los valores para futuras referencias</span><span class="sxs-lookup"><span data-stu-id="fcf08-181">Record values for future reference</span></span>

<span data-ttu-id="fcf08-182">Anote estos valores para trabajar con o implementar Guías del entorno de pruebas adicionales en este entorno de prueba:</span><span class="sxs-lookup"><span data-stu-id="fcf08-182">Record these values for working with or deploying additional Test Lab Guides in this test environment:</span></span>
  
- <span data-ttu-id="fcf08-183">Nombre del administrador global de Office 365: ![](./media/Common-Images/TableLine.png).onmicrosoft.com (del paso 9 de la fase 2)</span><span class="sxs-lookup"><span data-stu-id="fcf08-183">Office 365 global administrator name: ![](./media/Common-Images/TableLine.png).onmicrosoft.com (from step 9 of Phase 2)</span></span>
    
    <span data-ttu-id="fcf08-184">Guarde también la contraseña de esta cuenta en una ubicación segura.</span><span class="sxs-lookup"><span data-stu-id="fcf08-184">Also record the password for this account in a secure location.</span></span>
    
- <span data-ttu-id="fcf08-185">Nombre de la organización de la suscripción de prueba: ![](./media/Common-Images/TableLine.png) (del paso 4 de la fase 2)</span><span class="sxs-lookup"><span data-stu-id="fcf08-185">Your trial subscription organization name: ![](./media/Common-Images/TableLine.png) (from step 4 of Phase 2)</span></span>
    
- <span data-ttu-id="fcf08-186">Para mostrar las cuentas de los usuarios 2, 3, 4 y 5, ejecute los siguientes comandos desde el símbolo del sistema del Módulo de Windows Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fcf08-186">To list the accounts for User 2, User 3, User 4, and User 5, run the following command from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
    
  ```
  Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    <span data-ttu-id="fcf08-187">Anote aquí los nombres de las cuentas:</span><span class="sxs-lookup"><span data-stu-id="fcf08-187">Record the account names here:</span></span>
    
  - <span data-ttu-id="fcf08-188">Nombre de la cuenta de usuario 2: usuario2@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="fcf08-188">User 2 account name: user2@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span></span>
    
  - <span data-ttu-id="fcf08-189">Nombre de la cuenta de usuario 3: usuario3@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="fcf08-189">User 3 account name: user3@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span></span>
    
  - <span data-ttu-id="fcf08-190">Nombre de la cuenta de usuario 4: usuario4@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="fcf08-190">User 4 account name: user4@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span></span>
    
  - <span data-ttu-id="fcf08-191">Nombre de la cuenta de usuario 5: usuario5@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="fcf08-191">User 5 account name: user5@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span></span>
    
    <span data-ttu-id="fcf08-192">Guarde también las contraseñas de estas cuentas en una ubicación segura.</span><span class="sxs-lookup"><span data-stu-id="fcf08-192">Also record the passwords for these accounts in a secure location.</span></span>
    
- <span data-ttu-id="fcf08-193">(opcional) Para mostrar las direcciones URL de los sitios de grupo de Ventas, Producción y Soporte técnico, ejecute el comando siguiente desde el símbolo del sistema del Shell de administración de SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="fcf08-193">(optional) To list the URLs for the Sales, Production, and Support team sites, run the following command from the SharePoint Online Management Shell prompt:</span></span>
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

  - <span data-ttu-id="fcf08-194">Dirección URL del sitio de producción: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/production</span><span class="sxs-lookup"><span data-stu-id="fcf08-194">Production site URL: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/production</span></span>
    
  - <span data-ttu-id="fcf08-195">Dirección URL del sitio de ventas: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/sales</span><span class="sxs-lookup"><span data-stu-id="fcf08-195">Sales site URL: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/sales</span></span>
    
  - <span data-ttu-id="fcf08-196">Dirección URL del sitio de soporte técnico: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/support</span><span class="sxs-lookup"><span data-stu-id="fcf08-196">Support site URL: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/support</span></span>
    
## <a name="next-steps"></a><span data-ttu-id="fcf08-197">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="fcf08-197">Next steps</span></span>

<span data-ttu-id="fcf08-198">Use estos artículos adicionales en el entorno de desarrollo y pruebas de Office 365:</span><span class="sxs-lookup"><span data-stu-id="fcf08-198">Use these additional articles in your Office 365 dev/test environment:</span></span>
  
- [<span data-ttu-id="fcf08-199">Configurar la sincronización de directorios para el entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="fcf08-199">Directory Synchronization for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="fcf08-200">Autenticación multifactor para el entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="fcf08-200">Multi-factor authentication for your Office 365 dev/test environment</span></span>](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="fcf08-201">Identidad federada para el entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="fcf08-201">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="fcf08-202">Cloud App Security para el entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="fcf08-202">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="fcf08-203">Protección contra amenazas avanzada en el entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="fcf08-203">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="fcf08-204">eDiscovery avanzado para el entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="fcf08-204">Advanced eDiscovery for your Office 365 dev/test environment</span></span>](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="fcf08-205">Protección de archivos confidenciales en el entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="fcf08-205">Sensitive file protection in the Office 365 dev/test environment</span></span>](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="fcf08-206">Sitio de grupo de SharePoint Online aislado en el entorno de desarrollo y pruebas</span><span class="sxs-lookup"><span data-stu-id="fcf08-206">Isolated SharePoint Online team site dev/test environment</span></span>](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
- [<span data-ttu-id="fcf08-207">Etiquetado y clasificación de datos en el entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="fcf08-207">Data classification and labeling in the Office 365 dev/test environment</span></span>](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
<span data-ttu-id="fcf08-208">Extienda el entorno de desarrollo y pruebas de Office 365 para incluir ofertas adicionales en la nube de Microsoft:</span><span class="sxs-lookup"><span data-stu-id="fcf08-208">Extend your Office 365 dev/test environment to include additional Microsoft cloud offerings:</span></span>
  
- [<span data-ttu-id="fcf08-209">Entorno de desarrollo y pruebas de Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="fcf08-209">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
    
- [<span data-ttu-id="fcf08-210">Entorno de desarrollo y pruebas de Office 365 y Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="fcf08-210">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
    
## <a name="see-also"></a><span data-ttu-id="fcf08-211">Vea también</span><span class="sxs-lookup"><span data-stu-id="fcf08-211">See Also</span></span>

- [<span data-ttu-id="fcf08-212">Guías del entorno de pruebas de adopción de la nube (TLG)</span><span class="sxs-lookup"><span data-stu-id="fcf08-212">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
- [<span data-ttu-id="fcf08-213">Entorno de desarrollo y pruebas de Office 365 y Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="fcf08-213">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
  
- [<span data-ttu-id="fcf08-214">Adopción de la nube y soluciones híbridas</span><span class="sxs-lookup"><span data-stu-id="fcf08-214">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


