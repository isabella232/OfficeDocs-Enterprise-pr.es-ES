---
title: Administración de grupos de Microsoft 365 con PowerShell
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords: CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BSA160
- BCS160
ms.assetid: aeb669aa-1770-4537-9de2-a82ac11b0540
description: Obtenga información sobre cómo realizar tareas de administración comunes para los grupos de Microsoft 365 en Microsoft PowerShell.
ms.openlocfilehash: e0758ca928a30c06da33f0b213ada51f69bf65e1
ms.sourcegitcommit: 6b12e3ab76809d5632923def7ee367cd48ef3ccc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2020
ms.locfileid: "45117262"
---
# <a name="manage-microsoft-365-groups-with-powershell"></a><span data-ttu-id="95be1-103">Administración de grupos de Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="95be1-103">Manage Microsoft 365 Groups with PowerShell</span></span>
 
<span data-ttu-id="95be1-104">En este artículo se describen los pasos para realizar tareas de administración comunes para los grupos de Microsoft PowerShell.</span><span class="sxs-lookup"><span data-stu-id="95be1-104">This article provides the steps for doing common management tasks for Groups in Microsoft PowerShell.</span></span> <span data-ttu-id="95be1-105">También muestra los cmdlets de PowerShell para grupos.</span><span class="sxs-lookup"><span data-stu-id="95be1-105">It also lists the PowerShell cmdlets for Groups.</span></span> <span data-ttu-id="95be1-106">Para obtener información sobre la administración de sitios de SharePoint, vea [administrar sitios de SharePoint Online con PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).</span><span class="sxs-lookup"><span data-stu-id="95be1-106">For info about managing SharePoint sites, see [Manage SharePoint Online sites using PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).</span></span>

## <a name="link-to-your-microsoft-365-groups-usage-guidelines"></a><span data-ttu-id="95be1-107">Vínculo a las instrucciones de uso de Microsoft 365 Groups</span><span class="sxs-lookup"><span data-stu-id="95be1-107">Link to your Microsoft 365 Groups usage guidelines</span></span>
<span data-ttu-id="95be1-108"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="95be1-108"><a name="BK_LinkToGuideLines"> </a></span></span>

<span data-ttu-id="95be1-109">Cuando los usuarios [creen o editen un grupo en Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), podrá mostrarles un vínculo a las instrucciones de uso de su organización.</span><span class="sxs-lookup"><span data-stu-id="95be1-109">When users [create or edit a group in Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), you can show them a link to your organization's usage guidelines.</span></span> <span data-ttu-id="95be1-110">Por ejemplo, si necesita agregar un prefijo o un sufijo específico a un nombre de grupo.</span><span class="sxs-lookup"><span data-stu-id="95be1-110">For example, if you require a specific prefix or suffix to be added to a group name.</span></span>
  
<span data-ttu-id="95be1-111">Use Azure Active Directory (Azure AD) PowerShell para apuntar a los usuarios a las directrices de uso de su organización para los grupos de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="95be1-111">Use the Azure Active Directory (Azure AD) PowerShell to point your users to your organization's usage guidelines for Microsoft 365 groups.</span></span> <span data-ttu-id="95be1-112">Consulte [Azure Active Directory cmdlets para configurar las opciones de grupo](https://go.microsoft.com/fwlink/?LinkID=827484) y siga los pasos que se indican en el vínculo **crear configuración a nivel de directorio** para definir el hipervínculo de la instrucción de uso.</span><span class="sxs-lookup"><span data-stu-id="95be1-112">Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the usage guideline hyperlink.</span></span> <span data-ttu-id="95be1-113">Una vez que se haya ejecutado el cmdlet de AAD, el usuario verá el vínculo a las directrices al crear o editar un grupo en Outlook.</span><span class="sxs-lookup"><span data-stu-id="95be1-113">Once you run the AAD cmdlet, user's will see the link to your guidelines when they create or edit a group in Outlook.</span></span> 
  
![Crear un nuevo grupo con el vínculo de instrucciones de uso](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![Haga clic en instrucciones de uso de grupos para ver las directrices de grupos de Office 365](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
## <a name="allow-users-to-send-as-the-microsoft-365-group"></a><span data-ttu-id="95be1-116">Permitir a los usuarios enviar como grupo de 365 de Microsoft</span><span class="sxs-lookup"><span data-stu-id="95be1-116">Allow users to Send as the Microsoft 365 Group</span></span>
<span data-ttu-id="95be1-117"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="95be1-117"><a name="BK_LinkToGuideLines"> </a></span></span>
  
<span data-ttu-id="95be1-118">Si desea habilitar los grupos de Microsoft 365 para "enviar como", use los cmdlets [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/Add-RecipientPermission) y [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/Get-Recipient) para configurarlos.</span><span class="sxs-lookup"><span data-stu-id="95be1-118">If you want to enable your Microsoft 365 groups to "Send As", use the [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/Add-RecipientPermission) and the [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/Get-Recipient) cmdlets to configure this.</span></span> <span data-ttu-id="95be1-119">Una vez habilitada esta opción, los usuarios del grupo de 365 de Microsoft pueden usar Outlook o Outlook en la web para enviar y responder correo electrónico como el grupo de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="95be1-119">Once you enable this setting, Microsoft 365 group users can use Outlook or Outlook on the web to send and reply to email as the Microsoft 365 group.</span></span> <span data-ttu-id="95be1-120">Los usuarios pueden ir al grupo, crear un nuevo correo electrónico y cambiar el campo "enviar como" por la dirección de correo electrónico del grupo.</span><span class="sxs-lookup"><span data-stu-id="95be1-120">Users can go to the group, create a new email, and change the "Send As" field to the group's email address.</span></span> 

<span data-ttu-id="95be1-121">([También puede hacerlo en el centro de administración de Exchange](https://docs.microsoft.com/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group)).</span><span class="sxs-lookup"><span data-stu-id="95be1-121">([You can also do this in the Exchange Admin Center](https://docs.microsoft.com/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group).)</span></span>
  
<span data-ttu-id="95be1-122">Use el siguiente script, reemplazando *\<GroupAlias\>* por el alias del grupo que desea actualizar y *\<UserAlias\>* con el alias del usuario al que desea conceder permisos.</span><span class="sxs-lookup"><span data-stu-id="95be1-122">Use the following script, replacing *\<GroupAlias\>* with the alias of the group that you want to update, and *\<UserAlias\>* with the alias of the user to whom you want to grant permissions.</span></span> <span data-ttu-id="95be1-123">[Conéctese a Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) para ejecutar este script.</span><span class="sxs-lookup"><span data-stu-id="95be1-123">[Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) to run this script.</span></span>

```PowerShell
$groupAlias = "<GroupAlias>"

$userAlias = "<UserAlias>"


$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

<span data-ttu-id="95be1-124">Una vez que se ejecuta el cmdlet, los usuarios pueden ir a Outlook o Outlook en la web para enviarlos como grupo, agregando la dirección de correo electrónico del grupo al campo **de** .</span><span class="sxs-lookup"><span data-stu-id="95be1-124">Once the cmdlet is executed, users can go to Outlook or Outlook on the web to send as the group, by adding the group email address to the **From** field.</span></span> 

## <a name="create-classifications-for-office-groups-in-your-organization"></a><span data-ttu-id="95be1-125">Crear clasificaciones para los grupos de Office en su organización</span><span class="sxs-lookup"><span data-stu-id="95be1-125">Create classifications for Office groups in your organization</span></span>

<span data-ttu-id="95be1-126">Puede crear etiquetas de confidencialidad que los usuarios de su organización puedan establecer al crear un grupo de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="95be1-126">You can create sensitivity labels that the users in your organization can set when they create a Microsoft 365 Group.</span></span> <span data-ttu-id="95be1-127">Si desea clasificar grupos, se recomienda usar etiquetas de confidencialidad en lugar de la característica de clasificación de grupos anterior.</span><span class="sxs-lookup"><span data-stu-id="95be1-127">If you want to classify groups, we recommend using sensitivity labels instead of the previous groups classification feature.</span></span> <span data-ttu-id="95be1-128">Para obtener información sobre el uso de las etiquetas de confidencialidad, consulte [usar las etiquetas de confidencialidad para proteger el contenido en Microsoft Teams, grupos de microsoft 365 y sitios de SharePoint](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites).</span><span class="sxs-lookup"><span data-stu-id="95be1-128">For information about using sensitivity labels, see [Use sensitivity labels to protect content in Microsoft Teams, Microsoft 365 groups, and SharePoint sites](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="95be1-129">Si actualmente usa etiquetas de clasificación, ya no estarán disponibles para los usuarios que crean grupos cuando las etiquetas de confidencialidad están habilitadas.</span><span class="sxs-lookup"><span data-stu-id="95be1-129">If you are currently using classification labels, they will no longer be available to users who create groups once sensitivity labels are enabled.</span></span>

<span data-ttu-id="95be1-130">Todavía puede usar la característica clasificación de grupos anterior.</span><span class="sxs-lookup"><span data-stu-id="95be1-130">You can still use the previous groups classification feature.</span></span> <span data-ttu-id="95be1-131">Puede crear clasificaciones que los usuarios de la organización pueden establecer al crear un grupo de Office 365.</span><span class="sxs-lookup"><span data-stu-id="95be1-131">You can create classifications that the users in your organization can set when they create an Office 365 group.</span></span> <span data-ttu-id="95be1-132">Por ejemplo, puede permitir que los usuarios establezcan "Standard", "Secret" y "Top Secret" en los grupos que crean.</span><span class="sxs-lookup"><span data-stu-id="95be1-132">For example, you can allow users to set "Standard", "Secret", and "Top Secret" on groups they create.</span></span> <span data-ttu-id="95be1-133">Las clasificaciones de grupo no se establecen de forma predeterminada y es necesario crearlas para que los usuarios las configuren.</span><span class="sxs-lookup"><span data-stu-id="95be1-133">Group classifications aren't set by default and you need to create it in order for your users to set it.</span></span> <span data-ttu-id="95be1-134">Use Azure Active Directory PowerShell para dirigir a los usuarios a las instrucciones de uso de la organización para los grupos de Office 365.</span><span class="sxs-lookup"><span data-stu-id="95be1-134">Use Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups.</span></span>
  
<span data-ttu-id="95be1-135">Consulte los [cmdlets de Azure Active Directory para configurar las opciones de grupo](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) y siga los pasos descritos en la **opción crear configuración a nivel de directorio** para definir la clasificación de los grupos de Office 365.</span><span class="sxs-lookup"><span data-stu-id="95be1-135">Check out [Azure Active Directory cmdlets for configuring group settings](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) and follow the steps in the **Create settings at the directory level** to define the classification for Office 365 groups.</span></span> 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

<span data-ttu-id="95be1-136">Para asociar una descripción a cada clasificación, puede usar el atributo Settings *ClassificationDescriptions* para definirla.</span><span class="sxs-lookup"><span data-stu-id="95be1-136">In order to associate a description to each classification you can use the settings attribute  *ClassificationDescriptions* to define.</span></span>
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

<span data-ttu-id="95be1-137">donde clasificación coincide con las cadenas de ClassificationList.</span><span class="sxs-lookup"><span data-stu-id="95be1-137">where Classification matches the strings in the ClassificationList.</span></span>

<span data-ttu-id="95be1-138">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="95be1-138">Example:</span></span>
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

<span data-ttu-id="95be1-139">Después de ejecutar el cmdlet de Azure Active Directory anterior para establecer la clasificación, ejecute el cmdlet [set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/Set-UnifiedGroup) si desea establecer la clasificación para un grupo específico.</span><span class="sxs-lookup"><span data-stu-id="95be1-139">After you run the above Azure Active Directory cmdlet to set your classification, run the [Set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/Set-UnifiedGroup) cmdlet if you want to set the classification for a specific group.</span></span> 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

<span data-ttu-id="95be1-140">O bien, cree un nuevo grupo con una clasificación.</span><span class="sxs-lookup"><span data-stu-id="95be1-140">Or create a new group with a classification.</span></span>
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

<span data-ttu-id="95be1-141">Vea [usar PowerShell con Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) y [Conéctese a Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) para obtener más información sobre el uso de Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="95be1-141">Check out [Using PowerShell with Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) and [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) for more details on using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="95be1-142">Una vez habilitada esta configuración, el propietario del grupo podrá elegir una clasificación en el menú desplegable de Outlook en la web y en Outlook, y guardarla desde la página **Editar** grupo.</span><span class="sxs-lookup"><span data-stu-id="95be1-142">Once these settings are enabled, the group owner will be able to choose a classification from the drop down menu in Outlook on the Web and Outlook, and save it from the **Edit** group page.</span></span> 
  
![Elegir la clasificación de grupo de Office 365](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
## <a name="hide-office-365-groups-from-gal"></a><span data-ttu-id="95be1-144">Ocultar grupos de Office 365 desde GAL</span><span class="sxs-lookup"><span data-stu-id="95be1-144">Hide Office 365 Groups from GAL</span></span>
<span data-ttu-id="95be1-145"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="95be1-145"><a name="BKMK_CreateClassification"> </a></span></span>

<span data-ttu-id="95be1-146">Puede especificar si un grupo de Office 365 aparece en la lista global de direcciones (GAL) y en otras listas de la organización.</span><span class="sxs-lookup"><span data-stu-id="95be1-146">You can specify whether an Office 365 group appears in the global address list (GAL) and other lists in your organization.</span></span> <span data-ttu-id="95be1-147">Por ejemplo, si tiene un grupo de departamento legal que no desea que aparezca en la lista de direcciones, puede impedir que ese grupo aparezca en la GAL.</span><span class="sxs-lookup"><span data-stu-id="95be1-147">For example, if you have a legal department group that you don't want to show up in the address list, you can stop that group from appearing in GAL.</span></span> <span data-ttu-id="95be1-148">Ejecute el cmdlet Set-Unified Group para ocultar el grupo de la lista de direcciones de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="95be1-148">Run the Set-Unified Group cmdlet to hide the group from address list like this:</span></span>
  
```
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a><span data-ttu-id="95be1-149">Permitir que solo los usuarios internos envíen mensajes al grupo de Office 365</span><span class="sxs-lookup"><span data-stu-id="95be1-149">Allow only internal users to send message to Office 365 group</span></span>
<span data-ttu-id="95be1-150"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="95be1-150"><a name="BKMK_CreateClassification"> </a></span></span>

<span data-ttu-id="95be1-151">Si no desea que los usuarios de otras organizaciones envíen correo electrónico a un grupo de Office 365, puede cambiar la configuración de ese grupo.</span><span class="sxs-lookup"><span data-stu-id="95be1-151">If you don't want users from other organization to send email to an Office 365 group, you can change the settings for that group.</span></span> <span data-ttu-id="95be1-152">Permitirá que solo los usuarios internos envíen un correo electrónico a su grupo.</span><span class="sxs-lookup"><span data-stu-id="95be1-152">It will allow only internal users to send an email to your group.</span></span> <span data-ttu-id="95be1-153">Si un usuario externo intenta enviar un mensaje a ese grupo, se rechazará.</span><span class="sxs-lookup"><span data-stu-id="95be1-153">If external user try to send message to that group they will be rejected.</span></span>
  
<span data-ttu-id="95be1-154">Ejecute el cmdlet Set-UnifiedGroup para actualizar esta configuración, como se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="95be1-154">Run the Set-UnifiedGroup cmdlet to update this setting, like this:</span></span>

```
Set-UnifiedGroup -Identity "Internal senders only" -RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-the-office-365-groups"></a><span data-ttu-id="95be1-155">Agregar sugerencias de correo a los grupos de Office 365</span><span class="sxs-lookup"><span data-stu-id="95be1-155">Add MailTips to the Office 365 Groups</span></span>
<span data-ttu-id="95be1-156"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="95be1-156"><a name="BKMK_CreateClassification"> </a></span></span>

<span data-ttu-id="95be1-157">Cuando un remitente intenta enviar un correo electrónico a un grupo de Office 365, se le puede mostrar una sugerencia de correo electrónico.</span><span class="sxs-lookup"><span data-stu-id="95be1-157">Whenever a sender tries to send an email to an Office 365 group, a MailTip can be shown to them.</span></span>
  
<span data-ttu-id="95be1-158">Ejecute el cmdlet Set-Unified Group para agregar una sugerencia de correo al Grupo:</span><span class="sxs-lookup"><span data-stu-id="95be1-158">Run the Set-Unified Group cmdlet to add a mailTip to the group:</span></span>

```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

<span data-ttu-id="95be1-159">Además de la sugerencia de correo, también puede establecer MailTipTranslations, que especifica los idiomas adicionales para la sugerencia de correo.</span><span class="sxs-lookup"><span data-stu-id="95be1-159">Along with MailTip, you can also set MailTipTranslations, which specifies additional languages for the MailTip.</span></span> <span data-ttu-id="95be1-160">Suponga que quiere tener la traducción al español y, a continuación, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="95be1-160">Suppose you want to have the Spanish translation, then run the following command:</span></span>
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-display-name-of-the-office-365-group"></a><span data-ttu-id="95be1-161">Cambiar el nombre para mostrar del grupo de Office 365</span><span class="sxs-lookup"><span data-stu-id="95be1-161">Change Display name of the Office 365 group</span></span>

<span data-ttu-id="95be1-162">Nombre para mostrar especifica el nombre del grupo de Office 365.</span><span class="sxs-lookup"><span data-stu-id="95be1-162">Display name specifies the name of the Office 365 group.</span></span> <span data-ttu-id="95be1-163">Puede ver este nombre en su centro de administración de Exchange o en el centro de administración de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="95be1-163">You can see this name in your exchange admin center or Microsoft 365 admin center.</span></span> <span data-ttu-id="95be1-164">Puede editar el nombre para mostrar del grupo o asignar un nombre para mostrar a un grupo existente de Office 365 mediante la ejecución del comando set-UnifiedGroup:</span><span class="sxs-lookup"><span data-stu-id="95be1-164">You can edit the display name of the group or assign a display name to an existing Office 365 group by running the Set-UnifiedGroup command:</span></span>

```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a><span data-ttu-id="95be1-165">Cambiar la configuración predeterminada de Office 365 Groups para Outlook a Public o Private</span><span class="sxs-lookup"><span data-stu-id="95be1-165">Change the default setting of Office 365 Groups for Outlook to Public or Private</span></span>
<span data-ttu-id="95be1-166"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="95be1-166"><a name="BKMK_CreateClassification"> </a></span></span>

<span data-ttu-id="95be1-167">Office 365 grupos en Outlook se crean como privados de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="95be1-167">Office 365 Groups in Outlook are created as Private by default.</span></span> <span data-ttu-id="95be1-168">Si su organización desea que los grupos de Office 365 se creen como públicos de forma predeterminada (o volver a privado), use esta sintaxis de cmdlet de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="95be1-168">If your organization wants Office 365 Groups to be created as Public by default (or back to Private), use this PowerShell cmdlet syntax:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
<span data-ttu-id="95be1-169">Para establecer en privado:</span><span class="sxs-lookup"><span data-stu-id="95be1-169">To set to Private:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
<span data-ttu-id="95be1-170">Para comprobar la configuración:</span><span class="sxs-lookup"><span data-stu-id="95be1-170">To verify the setting:</span></span> 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
<span data-ttu-id="95be1-171">Para obtener más información, consulte [set-organizationconfig](https://docs.microsoft.com/powershell/module/exchange/set-organizationconfig) y [Get-organizationconfig](https://docs.microsoft.com/powershell/module/exchange/Get-OrganizationConfig).</span><span class="sxs-lookup"><span data-stu-id="95be1-171">To learn more, see [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/set-organizationconfig) and [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/Get-OrganizationConfig).</span></span>
  
## <a name="office-365-groups-cmdlets"></a><span data-ttu-id="95be1-172">Cmdlets de grupos de Office 365</span><span class="sxs-lookup"><span data-stu-id="95be1-172">Office 365 Groups cmdlets</span></span>

<span data-ttu-id="95be1-173">Los siguientes cmdlets se pueden usar con los grupos de Office 365.</span><span class="sxs-lookup"><span data-stu-id="95be1-173">The following cmdlets can be used with Office 365 Groups.</span></span>
  
|<span data-ttu-id="95be1-174">**Nombre de cmdlet**</span><span class="sxs-lookup"><span data-stu-id="95be1-174">**Cmdlet name**</span></span>|<span data-ttu-id="95be1-175">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="95be1-175">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="95be1-176">Get-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="95be1-176">Get-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |<span data-ttu-id="95be1-177">Use este cmdlet para buscar grupos existentes de Office 365 y para ver las propiedades del objeto de grupo.</span><span class="sxs-lookup"><span data-stu-id="95be1-177">Use this cmdlet to look up existing Office 365 Groups, and to view properties of the group object</span></span>  <br/> |
|[<span data-ttu-id="95be1-178">Set-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="95be1-178">Set-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |<span data-ttu-id="95be1-179">Actualizar las propiedades de un grupo específico de Office 365</span><span class="sxs-lookup"><span data-stu-id="95be1-179">Update the properties of a specific Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="95be1-180">New-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="95be1-180">New-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |<span data-ttu-id="95be1-181">Cree un nuevo grupo de Office 365.</span><span class="sxs-lookup"><span data-stu-id="95be1-181">Create a new Office 365 group.</span></span> <span data-ttu-id="95be1-182">Este cmdlet proporciona un conjunto mínimo de parámetros para establecer los valores de las propiedades extendidas usando Set-UnifiedGroup después de crear el nuevo grupo.</span><span class="sxs-lookup"><span data-stu-id="95be1-182">This cmdlet provides a minimal set of parameters, for setting values for extended properties use Set-UnifiedGroup after creating the new group</span></span>  <br/> |
|[<span data-ttu-id="95be1-183">Remove-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="95be1-183">Remove-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |<span data-ttu-id="95be1-184">Eliminar un grupo existente de Office 365</span><span class="sxs-lookup"><span data-stu-id="95be1-184">Delete an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="95be1-185">Get-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="95be1-185">Get-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |<span data-ttu-id="95be1-186">Recuperar la información de pertenencia y propietario de un grupo de Office 365</span><span class="sxs-lookup"><span data-stu-id="95be1-186">Retrieve membership and owner information for an Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="95be1-187">Add-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="95be1-187">Add-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |<span data-ttu-id="95be1-188">Agregar cientos o miles de usuarios, o propietarios nuevos, a un grupo existente de Office 365</span><span class="sxs-lookup"><span data-stu-id="95be1-188">Add hundred or thousands of users, or new owners, to an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="95be1-189">Remove-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="95be1-189">Remove-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |<span data-ttu-id="95be1-190">Quitar propietarios y miembros de un grupo existente de Office 365</span><span class="sxs-lookup"><span data-stu-id="95be1-190">Remove owners and members from an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="95be1-191">Get-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="95be1-191">Get-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |<span data-ttu-id="95be1-192">Se usa para ver información sobre la foto de usuario asociada a una cuenta.</span><span class="sxs-lookup"><span data-stu-id="95be1-192">Used to view information about the user photo associated with an account.</span></span> <span data-ttu-id="95be1-193">Las fotos de los usuarios se almacenan en Active Directory</span><span class="sxs-lookup"><span data-stu-id="95be1-193">User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="95be1-194">Set-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="95be1-194">Set-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |<span data-ttu-id="95be1-195">Se usa para asociar una foto de usuario con una cuenta.</span><span class="sxs-lookup"><span data-stu-id="95be1-195">Used to associate a user photo with an account.</span></span> <span data-ttu-id="95be1-196">Las fotos de los usuarios se almacenan en Active Directory</span><span class="sxs-lookup"><span data-stu-id="95be1-196">User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="95be1-197">Remove-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="95be1-197">Remove-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |<span data-ttu-id="95be1-198">Quitar la foto de un grupo de Office 365</span><span class="sxs-lookup"><span data-stu-id="95be1-198">Remove the photo for an Office 365 group</span></span>  <br/> |

## <a name="related-topics"></a><span data-ttu-id="95be1-199">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="95be1-199">Related topics</span></span>

[<span data-ttu-id="95be1-200">Actualizar listas de distribución a grupos de Office 365</span><span class="sxs-lookup"><span data-stu-id="95be1-200">Upgrade distribution lists to Office 365 Groups</span></span>](https://docs.microsoft.com/office365/admin/manage/upgrade-distribution-lists)

[<span data-ttu-id="95be1-201">Administrar quién puede crear grupos de Office 365</span><span class="sxs-lookup"><span data-stu-id="95be1-201">Manage who can create Office 365 Groups</span></span>](https://docs.microsoft.com/office365/admin/create-groups/manage-creation-of-groups)

[<span data-ttu-id="95be1-202">Administrar el acceso de invitados a los grupos de Office 365</span><span class="sxs-lookup"><span data-stu-id="95be1-202">Manage guest access to Office 365 Groups</span></span>](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[<span data-ttu-id="95be1-203">Cambiar la pertenencia al grupo estático a dinámico</span><span class="sxs-lookup"><span data-stu-id="95be1-203">Change static group membership to dynamic in</span></span>](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-change-type)
