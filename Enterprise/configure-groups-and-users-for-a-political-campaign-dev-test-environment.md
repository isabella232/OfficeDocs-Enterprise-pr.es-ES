---
title: "Configurar grupos y usuarios de un entorno de pruebas y desarrollo de campaña política"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: None
ms.custom: Strat_O365_Enterprise
ms.assetid: 0e22bcf3-bad3-42a4-b44f-276e0cf4790f
description: "Resumen: Crear suscripciones de prueba de seguridad (EMS) + Office 365 y movilidad en la empresa con usuarios y grupos para un entorno de pruebas y desarrollo de campaña política."
ms.openlocfilehash: adc5cdfe6d5c0c039ceb1c9068032fe2dae20114
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="configure-groups-and-users-for-a-political-campaign-devtest-environment"></a><span data-ttu-id="a91fb-103">Configurar grupos y usuarios de un entorno de pruebas y desarrollo de campaña política</span><span class="sxs-lookup"><span data-stu-id="a91fb-103">Configure groups and users for a political campaign dev/test environment</span></span>

 <span data-ttu-id="a91fb-104">**Resumen:** Crear suscripciones de prueba de seguridad (EMS) + Office 365 y movilidad en la empresa con usuarios y grupos para un entorno de pruebas y desarrollo de campaña política.</span><span class="sxs-lookup"><span data-stu-id="a91fb-104">**Summary:** Create Office 365 and Enterprise Mobility + Security (EMS) trial subscriptions with users and groups for a political campaign dev/test environment.</span></span>
  
<span data-ttu-id="a91fb-105">Utilice las instrucciones de este artículo para crear un entorno de pruebas y desarrollo que incluye las cuentas de usuario simplificado y grupos para la solución de [Microsoft Security Guidance for campañas políticos, las ONG y otras organizaciones ágiles](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) .</span><span class="sxs-lookup"><span data-stu-id="a91fb-105">Use the instructions in this article to create a dev/test environment that includes simplified user accounts and groups for the [Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) solution.</span></span>
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a><span data-ttu-id="a91fb-106">Fase 1: Crear el entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="a91fb-106">Phase 1: Create your Office 365 dev/test environment</span></span>

<span data-ttu-id="a91fb-107">En esta fase, se puede obtener las suscripciones de prueba de Office 365 E5 + E5 (EMS) de seguridad para una organización ficticia que representa una campaña política y movilidad en la empresa.</span><span class="sxs-lookup"><span data-stu-id="a91fb-107">In this phase, you obtain trial subscriptions for Office 365 E5 and Enterprise Mobility + Security (EMS) E5 for a fictional organization that represents a political campaign.</span></span>
  
<span data-ttu-id="a91fb-108">En primer lugar, siga las instrucciones en la **fase 2** del [entorno de desarrollo y prueba de Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="a91fb-108">First, follow the instructions in **Phase 2** of the [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="a91fb-109">A continuación, registrarse para la suscripción de prueba de EMS E5 y agregarlo a la misma organización que su suscripción de prueba de Office 365.</span><span class="sxs-lookup"><span data-stu-id="a91fb-109">Next, sign up for the EMS E5 trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="a91fb-p101">Si es necesario, iniciar sesión en el portal de Office 365 con las credenciales de la cuenta de administrador global de su suscripción de prueba. Para obtener ayuda, visite [dónde puede iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="a91fb-p101">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="a91fb-112">Haga clic en el mosaico de **Admin** .</span><span class="sxs-lookup"><span data-stu-id="a91fb-112">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="a91fb-113">En la ficha del **Centro de administración de Office** en el explorador, en la exploración de la izquierda, haga clic en **de facturación > adquirir servicios**.</span><span class="sxs-lookup"><span data-stu-id="a91fb-113">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="a91fb-p102">En la página **Servicios de compra** , busque el elemento de **seguridad E5 + de movilidad en la empresa** . Sitúe el puntero del mouse sobre él y haga clic en **iniciar la versión de prueba gratuita**.</span><span class="sxs-lookup"><span data-stu-id="a91fb-p102">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="a91fb-116">En la página **confirmar su pedido** , haga clic en **Probar ahora**.</span><span class="sxs-lookup"><span data-stu-id="a91fb-116">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="a91fb-117">En la página de **confirmación del pedido** , haga clic en **continuar**.</span><span class="sxs-lookup"><span data-stu-id="a91fb-117">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="a91fb-118">A continuación, habilite la licencia EMS E5 de la cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="a91fb-118">Next, enable the EMS E5 license for your global administrator account.</span></span>
  
1. <span data-ttu-id="a91fb-119">En la ficha del **Centro de administración de Office 365** en el explorador, en la exploración de la izquierda, haga clic en **los usuarios > usuarios activos**.</span><span class="sxs-lookup"><span data-stu-id="a91fb-119">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="a91fb-120">Haga clic en la cuenta de administrador global y, a continuación, haga clic en **Editar** para **licencias de producto**.</span><span class="sxs-lookup"><span data-stu-id="a91fb-120">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="a91fb-121">En el panel de **licencias de producto** , activar la licencia del producto de **movilidad en la empresa + seguridad E5** en **On**, haga clic en **Guardar** y, a continuación, haga clic en **Cerrar** dos veces.</span><span class="sxs-lookup"><span data-stu-id="a91fb-121">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups"></a><span data-ttu-id="a91fb-122">Fase 2: Crear y configurar los grupos de Azure de Active Directory (AD)</span><span class="sxs-lookup"><span data-stu-id="a91fb-122">Phase 2: Create and configure your Azure Active Directory (AD) groups</span></span>

<span data-ttu-id="a91fb-123">En esta fase, cree y configure los grupos de AD Azure para su campaña.</span><span class="sxs-lookup"><span data-stu-id="a91fb-123">In this phase, you create and configure the Azure AD groups for your campaign.</span></span>
  
<span data-ttu-id="a91fb-124">Primero, cree un conjunto de grupos para una campaña política típico con el portal de Azure.</span><span class="sxs-lookup"><span data-stu-id="a91fb-124">First, create a set of groups for a typical political campaign with the Azure portal.</span></span>
  
1. <span data-ttu-id="a91fb-125">En una ficha independiente en el explorador, vaya al portal de Azure en [https://portal.azure.com](https://portal.azure.com). Si es necesario, inicie sesión con las credenciales de la cuenta de administrador global para la suscripción de prueba de Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="a91fb-125">On a separate tab in your browser, go to the Azure portal at [https://portal.azure.com](https://portal.azure.com). If needed, sign in with the credentials of the global administrator account for your Office 365 E5 trial subscription.</span></span>
    
2. <span data-ttu-id="a91fb-126">En el portal de Azure, haga clic en **Azure Active Directory > usuarios y grupos > grupos de todos los**.</span><span class="sxs-lookup"><span data-stu-id="a91fb-126">In the Azure portal, click **Azure Active Directory > Users and groups > All groups**.</span></span>
    
3. <span data-ttu-id="a91fb-127">Realice los pasos siguientes para cada nombre de grupo en esta lista:</span><span class="sxs-lookup"><span data-stu-id="a91fb-127">Do the following steps for each group name in this list:</span></span>
    
  - <span data-ttu-id="a91fb-128">Director y el personal estratégico</span><span class="sxs-lookup"><span data-stu-id="a91fb-128">Senior and strategic staff</span></span>
    
  - <span data-ttu-id="a91fb-129">Personal de TI</span><span class="sxs-lookup"><span data-stu-id="a91fb-129">IT staff</span></span>
    
  - <span data-ttu-id="a91fb-130">Personal de análisis</span><span class="sxs-lookup"><span data-stu-id="a91fb-130">Analytics staff</span></span>
    
  - <span data-ttu-id="a91fb-131">Personal de base regular</span><span class="sxs-lookup"><span data-stu-id="a91fb-131">Regular core staff</span></span>
    
  - <span data-ttu-id="a91fb-132">Personal de operaciones</span><span class="sxs-lookup"><span data-stu-id="a91fb-132">Operations staff</span></span>
    
  - <span data-ttu-id="a91fb-133">Personal de campo</span><span class="sxs-lookup"><span data-stu-id="a91fb-133">Field staff</span></span>
    
1. <span data-ttu-id="a91fb-134">En la hoja de **todos los grupos** , haga clic en **+ nuevo grupo**.</span><span class="sxs-lookup"><span data-stu-id="a91fb-134">On the **All groups** blade, click **+ New group**.</span></span>
    
2. <span data-ttu-id="a91fb-135">En **nombre**, escriba el nombre del grupo de la lista.</span><span class="sxs-lookup"><span data-stu-id="a91fb-135">Type the group name from the list in **Name**.</span></span>
    
3. <span data-ttu-id="a91fb-136">Seleccione **usuario dinámica** de **pertenencia**.</span><span class="sxs-lookup"><span data-stu-id="a91fb-136">Select **Dynamic user** in **Membership**.</span></span>
    
4. <span data-ttu-id="a91fb-137">Haga clic en **Sí** para **Habilitar Office características**.</span><span class="sxs-lookup"><span data-stu-id="a91fb-137">Click **Yes** for **Enable Office features**.</span></span>
    
5. <span data-ttu-id="a91fb-138">Haga clic en **Agregar de consulta dinámica**.</span><span class="sxs-lookup"><span data-stu-id="a91fb-138">Click **Add dynamic query**.</span></span>
    
6. <span data-ttu-id="a91fb-139">En **Agregue usuarios donde**, seleccione **departamento**.</span><span class="sxs-lookup"><span data-stu-id="a91fb-139">In **Add users where**, select **department**.</span></span>
    
7. <span data-ttu-id="a91fb-140">En el siguiente campo, seleccione **igual a**.</span><span class="sxs-lookup"><span data-stu-id="a91fb-140">In the next field, select **Equals**.</span></span>
    
8. <span data-ttu-id="a91fb-141">En el siguiente campo, escriba el nombre del grupo de la lista.</span><span class="sxs-lookup"><span data-stu-id="a91fb-141">In the next field, type the group name from the list.</span></span>
    
9. <span data-ttu-id="a91fb-142">Haga clic en **Agregar consulta**y, a continuación, haga clic en **crear**.</span><span class="sxs-lookup"><span data-stu-id="a91fb-142">Click **Add query**, and then click **Create**.</span></span>
    
10. <span data-ttu-id="a91fb-143">Haga clic en **usuarios y grupos: todos los grupos**.</span><span class="sxs-lookup"><span data-stu-id="a91fb-143">Click **Users and groups - All groups**.</span></span>
    
<span data-ttu-id="a91fb-144">A continuación, configure los grupos para que los miembros se asignan automáticamente licencias Office 365 E5 y E5 EMS.</span><span class="sxs-lookup"><span data-stu-id="a91fb-144">Next, you configure the groups so that members are automatically assigned Office 365 E5 and EMS E5 licenses.</span></span>
  
1. <span data-ttu-id="a91fb-145">En el portal de Azure, haga clic en **Azure Active Directory > licencias > todos los productos**.</span><span class="sxs-lookup"><span data-stu-id="a91fb-145">In the Azure portal, click **Azure Active Directory > Licenses > All products**.</span></span>
    
2. <span data-ttu-id="a91fb-146">En la lista, seleccione **seguridad E5 + de movilidad en la empresa** y **E5 Enterprise de Office 365**y, a continuación, haga clic en **+ asignar**.</span><span class="sxs-lookup"><span data-stu-id="a91fb-146">In the list, select **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5**, and then click **+ Assign**.</span></span>
    
3. <span data-ttu-id="a91fb-147">En la hoja **asignar licencias** , haga clic en **usuarios y grupos**.</span><span class="sxs-lookup"><span data-stu-id="a91fb-147">In the **Assign license** blade, click **Users and groups**.</span></span>
    
4. <span data-ttu-id="a91fb-148">En la lista de grupos, seleccione lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="a91fb-148">In the list of groups, select the following:</span></span>
    
  - <span data-ttu-id="a91fb-149">Personal de análisis</span><span class="sxs-lookup"><span data-stu-id="a91fb-149">Analytics staff</span></span>
    
  - <span data-ttu-id="a91fb-150">Personal de campo</span><span class="sxs-lookup"><span data-stu-id="a91fb-150">Field staff</span></span>
    
  - <span data-ttu-id="a91fb-151">Personal de TI</span><span class="sxs-lookup"><span data-stu-id="a91fb-151">IT staff</span></span>
    
  - <span data-ttu-id="a91fb-152">Personal de operaciones</span><span class="sxs-lookup"><span data-stu-id="a91fb-152">Operations staff</span></span>
    
  - <span data-ttu-id="a91fb-153">Personal de base regular</span><span class="sxs-lookup"><span data-stu-id="a91fb-153">Regular core staff</span></span>
    
  - <span data-ttu-id="a91fb-154">Director y el personal estratégico</span><span class="sxs-lookup"><span data-stu-id="a91fb-154">Senior and strategic staff</span></span>
    
5. <span data-ttu-id="a91fb-155">Haga clic en **Seleccionar**y, a continuación, haga clic en **asignar**.</span><span class="sxs-lookup"><span data-stu-id="a91fb-155">Click **Select**, and then click **Assign**.</span></span>
    
6. <span data-ttu-id="a91fb-156">Cierre la ficha portal Azure en el explorador.</span><span class="sxs-lookup"><span data-stu-id="a91fb-156">Close the Azure portal tab in your browser.</span></span>
    
## <a name="phase-3-add-your-user-accounts"></a><span data-ttu-id="a91fb-157">Fase 3: Agregar las cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="a91fb-157">Phase 3: Add your user accounts</span></span>

<span data-ttu-id="a91fb-158">En esta fase, debe agregar las cuentas de usuario de ejemplo para su campaña política.</span><span class="sxs-lookup"><span data-stu-id="a91fb-158">In this phase, you add the example user accounts for your political campaign.</span></span>
  
<span data-ttu-id="a91fb-159">En primer lugar, puede [Conectar con el módulo de Active Directory V2 PowerShell de Azure](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="a91fb-159">First, you [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="a91fb-160">A continuación, rellene el nombre de su organización, su ubicación y una contraseña común y, a continuación, ejecutar estos comandos desde el símbolo del sistema de PowerShell o el entorno de secuencias de comandos integrado (ISE):</span><span class="sxs-lookup"><span data-stu-id="a91fb-160">Next, you fill in your organization name, your location, and a common password, and then run these commands from the PowerShell command prompt or Integrated Script Environment (ISE):</span></span>
  
```
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$deptName="Senior and strategic staff"
$userNames=@("Candidate","ChiefOfStaff","Strategic1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Analytics staff"
$userNames=@("DataScientist1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Regular core staff"
$userNames=@("Regular1","Regular2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Operations staff"
$userNames=@("Operations1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Field staff"
$userNames=@("FieldConsultant1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }

```

> [!IMPORTANT]
> <span data-ttu-id="a91fb-p103">El uso de una contraseña común aquí es para la automatización y la facilidad de configuración para un entorno de pruebas y desarrollo. Esto no es recomendable para las suscripciones de producción. Cuando se inscribe en cada una de estas nuevas cuentas de usuario, se le pedirá que cambie la contraseña.</span><span class="sxs-lookup"><span data-stu-id="a91fb-p103">The use of a common password here is for automation and ease of configuration for a dev/test environment. This is not recommended for production subscriptions. As you sign in with each of these new user accounts, you will be prompted to change the password.</span></span> 
  
<span data-ttu-id="a91fb-164">Siga estos pasos para comprobar que pertenencia a un grupo dinámico y basado en el grupo de licencias funciona correctamente.</span><span class="sxs-lookup"><span data-stu-id="a91fb-164">Use these steps to verify that dynamic group membership and group-based licensing are working correctly.</span></span>
  
1. <span data-ttu-id="a91fb-165">Desde la ficha **Página de inicio de Microsoft Office** del explorador, haga clic en el mosaico de **Admin** .</span><span class="sxs-lookup"><span data-stu-id="a91fb-165">From the **Microsoft Office Home** tab of your browser, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="a91fb-166">Desde la ficha del **Centro de administración de Office** nueva del explorador, haga clic en **usuarios**.</span><span class="sxs-lookup"><span data-stu-id="a91fb-166">From the new **Office Admin center** tab of your browser, click **Users**.</span></span>
    
3. <span data-ttu-id="a91fb-167">En la lista de usuarios, haga clic en **candidato**.</span><span class="sxs-lookup"><span data-stu-id="a91fb-167">In the list of users, click **Candidate**.</span></span>
    
4. <span data-ttu-id="a91fb-168">En el panel que muestra las propiedades de la cuenta de usuario de **candidato** , compruebe lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="a91fb-168">In the pane that lists the properties of the **Candidate** user account, verify that:</span></span>
    
  - <span data-ttu-id="a91fb-169">Es un miembro del grupo **jefe y personal estratégico** (en **pertenencia a grupos**).</span><span class="sxs-lookup"><span data-stu-id="a91fb-169">It is a member of the **Senior and strategic staff** group (in **Group memberships**).</span></span>
    
  - <span data-ttu-id="a91fb-170">Se le ha asignado las licencias de **movilidad en la empresa + seguridad E5** y **E5 Enterprise de Office 365** (en **licencias de producto**).</span><span class="sxs-lookup"><span data-stu-id="a91fb-170">It has been assigned the **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5** licenses (in **Product licenses**).</span></span>
    
5. <span data-ttu-id="a91fb-171">Cierre el panel de cuenta de usuario de **candidato** .</span><span class="sxs-lookup"><span data-stu-id="a91fb-171">Close the **Candidate** user account pane.</span></span>
    
## <a name="record-values-for-future-reference"></a><span data-ttu-id="a91fb-172">Anote los valores para futuras referencias</span><span class="sxs-lookup"><span data-stu-id="a91fb-172">Record values for future reference</span></span>

<span data-ttu-id="a91fb-173">Registre estos valores para trabajar con el Office 365 y EMS suscripciones de prueba para este entorno de pruebas y desarrollo:</span><span class="sxs-lookup"><span data-stu-id="a91fb-173">Record these values for working with the Office 365 and EMS trial subscriptions for this dev/test environment:</span></span>
  
- <span data-ttu-id="a91fb-174">Nombre de la organización de su suscripción de prueba: ___</span><span class="sxs-lookup"><span data-stu-id="a91fb-174">Your trial subscription organization name: _______________________________________________</span></span> 
    
    <span data-ttu-id="a91fb-175">Por ejemplo, el nombre de dominio de suscripción de prueba de contoso.onmicrosoft.com, el nombre de la organización es "contoso".</span><span class="sxs-lookup"><span data-stu-id="a91fb-175">For example, for the trial subscription domain name of contoso.onmicrosoft.com, the organization name is "contoso".</span></span>
    
- <span data-ttu-id="a91fb-176">El nombre de administrador global de Office 365: ___.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="a91fb-176">The Office 365 global administrator name: ____________________________________.onmicrosoft.com</span></span>
    
    <span data-ttu-id="a91fb-177">Registre la contraseña para esta cuenta y la contraseña inicial común para las otras cuentas de usuario en una ubicación segura.</span><span class="sxs-lookup"><span data-stu-id="a91fb-177">Record the password for this account and the common initial password for the other user accounts in a secure location.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="a91fb-178">Paso siguiente</span><span class="sxs-lookup"><span data-stu-id="a91fb-178">Next step</span></span>

<span data-ttu-id="a91fb-179">Crear los cuatro tipos diferentes de sitios de SharePoint Online team en este entorno de pruebas y desarrollo con [crear sitios de equipo en un entorno de pruebas y desarrollo de campaña política](create-team-sites-in-a-political-campaign-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="a91fb-179">Build the four different types of SharePoint Online team sites in this dev/test environment with [Create team sites in a political campaign dev/test environment](create-team-sites-in-a-political-campaign-dev-test-environment.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a91fb-180">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a91fb-180">See Also</span></span>

[<span data-ttu-id="a91fb-181">Guía de seguridad de Microsoft para campañas políticas, las ONG y otras organizaciones de Agile</span><span class="sxs-lookup"><span data-stu-id="a91fb-181">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="a91fb-182">Crear sitios de equipo en un entorno de pruebas y desarrollo de campaña política</span><span class="sxs-lookup"><span data-stu-id="a91fb-182">Create team sites in a political campaign dev/test environment</span></span>](create-team-sites-in-a-political-campaign-dev-test-environment.md)
  
[<span data-ttu-id="a91fb-183">Guías de entorno de pruebas de adopción de la nube (TLG)</span><span class="sxs-lookup"><span data-stu-id="a91fb-183">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="a91fb-184">Adopción de la nube y soluciones híbridas</span><span class="sxs-lookup"><span data-stu-id="a91fb-184">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




