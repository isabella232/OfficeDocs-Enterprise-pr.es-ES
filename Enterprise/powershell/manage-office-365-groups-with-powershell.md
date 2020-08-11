---
title: Administración de grupos de Microsoft 365 con PowerShell
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BSA160
- BCS160
ms.assetid: aeb669aa-1770-4537-9de2-a82ac11b0540
description: En este artículo, obtenga información sobre cómo realizar tareas de administración comunes para los grupos de Microsoft 365 en PowerShell.
ms.openlocfilehash: 899205fbf53821758f848fd4e1c75f25fd16e223
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605956"
---
# <a name="manage-microsoft-365-groups-with-powershell"></a><span data-ttu-id="24211-103">Administración de grupos de Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="24211-103">Manage Microsoft 365 Groups with PowerShell</span></span>
 
<span data-ttu-id="24211-104">*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="24211-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="24211-105">En este artículo se describen los pasos para realizar tareas de administración comunes para los grupos de Microsoft PowerShell.</span><span class="sxs-lookup"><span data-stu-id="24211-105">This article provides the steps for doing common management tasks for Groups in Microsoft PowerShell.</span></span> <span data-ttu-id="24211-106">También muestra los cmdlets de PowerShell para grupos.</span><span class="sxs-lookup"><span data-stu-id="24211-106">It also lists the PowerShell cmdlets for Groups.</span></span> <span data-ttu-id="24211-107">Para obtener información sobre la administración de sitios de SharePoint, vea [administrar sitios de SharePoint Online con PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).</span><span class="sxs-lookup"><span data-stu-id="24211-107">For info about managing SharePoint sites, see [Manage SharePoint Online sites using PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).</span></span>

## <a name="link-to-your-microsoft-365-groups-usage-guidelines"></a><span data-ttu-id="24211-108">Vínculo a las instrucciones de uso de Microsoft 365 Groups</span><span class="sxs-lookup"><span data-stu-id="24211-108">Link to your Microsoft 365 Groups usage guidelines</span></span>
<span data-ttu-id="24211-109"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="24211-109"><a name="BK_LinkToGuideLines"> </a></span></span>

<span data-ttu-id="24211-110">Cuando los usuarios [creen o editen un grupo en Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), podrá mostrarles un vínculo a las instrucciones de uso de su organización.</span><span class="sxs-lookup"><span data-stu-id="24211-110">When users [create or edit a group in Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), you can show them a link to your organization's usage guidelines.</span></span> <span data-ttu-id="24211-111">Por ejemplo, si necesita agregar un prefijo o un sufijo específico a un nombre de grupo.</span><span class="sxs-lookup"><span data-stu-id="24211-111">For example, if you require a specific prefix or suffix to be added to a group name.</span></span>
  
<span data-ttu-id="24211-112">Use Azure Active Directory (Azure AD) PowerShell para apuntar a los usuarios a las directrices de uso de su organización para los grupos de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="24211-112">Use the Azure Active Directory (Azure AD) PowerShell to point your users to your organization's usage guidelines for Microsoft 365 groups.</span></span> <span data-ttu-id="24211-113">Consulte [Azure Active Directory cmdlets para configurar las opciones de grupo](https://go.microsoft.com/fwlink/?LinkID=827484) y siga los pasos que se indican en el vínculo **crear configuración a nivel de directorio** para definir el hipervínculo de la instrucción de uso.</span><span class="sxs-lookup"><span data-stu-id="24211-113">Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the usage guideline hyperlink.</span></span> <span data-ttu-id="24211-114">Una vez que se haya ejecutado el cmdlet de AAD, el usuario verá el vínculo a las directrices al crear o editar un grupo en Outlook.</span><span class="sxs-lookup"><span data-stu-id="24211-114">Once you run the AAD cmdlet, user's will see the link to your guidelines when they create or edit a group in Outlook.</span></span> 
  
![Crear un nuevo grupo con el vínculo de instrucciones de uso](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![Haga clic en instrucciones de uso de grupos para ver las directrices de grupos de Office 365](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
## <a name="allow-users-to-send-as-the-microsoft-365-group"></a><span data-ttu-id="24211-117">Permitir a los usuarios enviar como grupo de 365 de Microsoft</span><span class="sxs-lookup"><span data-stu-id="24211-117">Allow users to Send as the Microsoft 365 Group</span></span>
<span data-ttu-id="24211-118"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="24211-118"><a name="BK_LinkToGuideLines"> </a></span></span>
  
<span data-ttu-id="24211-119">Si desea habilitar los grupos de Microsoft 365 para "enviar como", use los cmdlets [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/Add-RecipientPermission) y [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/Get-Recipient) para configurarlos.</span><span class="sxs-lookup"><span data-stu-id="24211-119">If you want to enable your Microsoft 365 groups to "Send As", use the [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/Add-RecipientPermission) and the [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/Get-Recipient) cmdlets to configure this.</span></span> <span data-ttu-id="24211-120">Una vez habilitada esta opción, los usuarios del grupo de 365 de Microsoft pueden usar Outlook o Outlook en la web para enviar y responder correo electrónico como el grupo de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="24211-120">Once you enable this setting, Microsoft 365 group users can use Outlook or Outlook on the web to send and reply to email as the Microsoft 365 group.</span></span> <span data-ttu-id="24211-121">Los usuarios pueden ir al grupo, crear un nuevo correo electrónico y cambiar el campo "enviar como" por la dirección de correo electrónico del grupo.</span><span class="sxs-lookup"><span data-stu-id="24211-121">Users can go to the group, create a new email, and change the "Send As" field to the group's email address.</span></span> 

<span data-ttu-id="24211-122">([También puede hacerlo en el centro de administración de Exchange](https://docs.microsoft.com/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group)).</span><span class="sxs-lookup"><span data-stu-id="24211-122">([You can also do this in the Exchange Admin Center](https://docs.microsoft.com/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group).)</span></span>
  
<span data-ttu-id="24211-123">Use el siguiente script, reemplazando *\<GroupAlias\>* por el alias del grupo que desea actualizar y *\<UserAlias\>* con el alias del usuario al que desea conceder permisos.</span><span class="sxs-lookup"><span data-stu-id="24211-123">Use the following script, replacing *\<GroupAlias\>* with the alias of the group that you want to update, and *\<UserAlias\>* with the alias of the user to whom you want to grant permissions.</span></span> <span data-ttu-id="24211-124">[Conéctese a Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) para ejecutar este script.</span><span class="sxs-lookup"><span data-stu-id="24211-124">[Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) to run this script.</span></span>

```PowerShell
$groupAlias = "<GroupAlias>"

$userAlias = "<UserAlias>"


$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

<span data-ttu-id="24211-125">Una vez que se ejecuta el cmdlet, los usuarios pueden ir a Outlook o Outlook en la web para enviarlos como grupo, agregando la dirección de correo electrónico del grupo al campo **de** .</span><span class="sxs-lookup"><span data-stu-id="24211-125">Once the cmdlet is executed, users can go to Outlook or Outlook on the web to send as the group, by adding the group email address to the **From** field.</span></span> 

## <a name="create-classifications-for-office-groups-in-your-organization"></a><span data-ttu-id="24211-126">Crear clasificaciones para los grupos de Office en su organización</span><span class="sxs-lookup"><span data-stu-id="24211-126">Create classifications for Office groups in your organization</span></span>

<span data-ttu-id="24211-127">Puede crear etiquetas de confidencialidad que los usuarios de su organización puedan establecer al crear un grupo de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="24211-127">You can create sensitivity labels that the users in your organization can set when they create a Microsoft 365 Group.</span></span> <span data-ttu-id="24211-128">Si desea clasificar grupos, se recomienda usar etiquetas de confidencialidad en lugar de la característica de clasificación de grupos anterior.</span><span class="sxs-lookup"><span data-stu-id="24211-128">If you want to classify groups, we recommend using sensitivity labels instead of the previous groups classification feature.</span></span> <span data-ttu-id="24211-129">Para obtener información sobre el uso de las etiquetas de confidencialidad, consulte [usar las etiquetas de confidencialidad para proteger el contenido en Microsoft Teams, grupos de microsoft 365 y sitios de SharePoint](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites).</span><span class="sxs-lookup"><span data-stu-id="24211-129">For information about using sensitivity labels, see [Use sensitivity labels to protect content in Microsoft Teams, Microsoft 365 groups, and SharePoint sites](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="24211-130">Si actualmente usa etiquetas de clasificación, ya no estarán disponibles para los usuarios que crean grupos cuando las etiquetas de confidencialidad están habilitadas.</span><span class="sxs-lookup"><span data-stu-id="24211-130">If you are currently using classification labels, they will no longer be available to users who create groups once sensitivity labels are enabled.</span></span>

<span data-ttu-id="24211-131">Todavía puede usar la característica clasificación de grupos anterior.</span><span class="sxs-lookup"><span data-stu-id="24211-131">You can still use the previous groups classification feature.</span></span> <span data-ttu-id="24211-132">Puede crear clasificaciones que los usuarios de la organización pueden establecer al crear un grupo de Office 365.</span><span class="sxs-lookup"><span data-stu-id="24211-132">You can create classifications that the users in your organization can set when they create an Office 365 group.</span></span> <span data-ttu-id="24211-133">Por ejemplo, puede permitir que los usuarios establezcan "Standard", "Secret" y "Top Secret" en los grupos que crean.</span><span class="sxs-lookup"><span data-stu-id="24211-133">For example, you can allow users to set "Standard", "Secret", and "Top Secret" on groups they create.</span></span> <span data-ttu-id="24211-134">Las clasificaciones de grupo no se establecen de forma predeterminada y es necesario crearlas para que los usuarios las configuren.</span><span class="sxs-lookup"><span data-stu-id="24211-134">Group classifications aren't set by default and you need to create it in order for your users to set it.</span></span> <span data-ttu-id="24211-135">Use Azure Active Directory PowerShell para dirigir a los usuarios a las instrucciones de uso de la organización para los grupos de Office 365.</span><span class="sxs-lookup"><span data-stu-id="24211-135">Use Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups.</span></span>
  
<span data-ttu-id="24211-136">Consulte los [cmdlets de Azure Active Directory para configurar las opciones de grupo](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) y siga los pasos descritos en la **opción crear configuración a nivel de directorio** para definir la clasificación de los grupos de Office 365.</span><span class="sxs-lookup"><span data-stu-id="24211-136">Check out [Azure Active Directory cmdlets for configuring group settings](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) and follow the steps in the **Create settings at the directory level** to define the classification for Office 365 groups.</span></span> 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

<span data-ttu-id="24211-137">Para asociar una descripción a cada clasificación, puede usar el atributo Settings *ClassificationDescriptions* para definirla.</span><span class="sxs-lookup"><span data-stu-id="24211-137">In order to associate a description to each classification you can use the settings attribute  *ClassificationDescriptions* to define.</span></span>
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

<span data-ttu-id="24211-138">donde clasificación coincide con las cadenas de ClassificationList.</span><span class="sxs-lookup"><span data-stu-id="24211-138">where Classification matches the strings in the ClassificationList.</span></span>

<span data-ttu-id="24211-139">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="24211-139">Example:</span></span>
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

<span data-ttu-id="24211-140">Después de ejecutar el cmdlet de Azure Active Directory anterior para establecer la clasificación, ejecute el cmdlet [set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/Set-UnifiedGroup) si desea establecer la clasificación para un grupo específico.</span><span class="sxs-lookup"><span data-stu-id="24211-140">After you run the above Azure Active Directory cmdlet to set your classification, run the [Set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/Set-UnifiedGroup) cmdlet if you want to set the classification for a specific group.</span></span> 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

<span data-ttu-id="24211-141">O bien, cree un nuevo grupo con una clasificación.</span><span class="sxs-lookup"><span data-stu-id="24211-141">Or create a new group with a classification.</span></span>
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

<span data-ttu-id="24211-142">Vea [usar PowerShell con Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) y [Conéctese a Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) para obtener más información sobre el uso de Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="24211-142">Check out [Using PowerShell with Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) and [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) for more details on using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="24211-143">Una vez habilitada esta configuración, el propietario del grupo podrá elegir una clasificación en el menú desplegable de Outlook en la web y en Outlook, y guardarla desde la página **Editar** grupo.</span><span class="sxs-lookup"><span data-stu-id="24211-143">Once these settings are enabled, the group owner will be able to choose a classification from the drop down menu in Outlook on the Web and Outlook, and save it from the **Edit** group page.</span></span> 
  
![Elegir la clasificación de grupo de Office 365](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
## <a name="hide-office-365-groups-from-gal"></a><span data-ttu-id="24211-145">Ocultar grupos de Office 365 desde GAL</span><span class="sxs-lookup"><span data-stu-id="24211-145">Hide Office 365 Groups from GAL</span></span>
<span data-ttu-id="24211-146"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="24211-146"><a name="BKMK_CreateClassification"> </a></span></span>

<span data-ttu-id="24211-147">Puede especificar si un grupo de Office 365 aparece en la lista global de direcciones (GAL) y en otras listas de la organización.</span><span class="sxs-lookup"><span data-stu-id="24211-147">You can specify whether an Office 365 group appears in the global address list (GAL) and other lists in your organization.</span></span> <span data-ttu-id="24211-148">Por ejemplo, si tiene un grupo de departamento legal que no desea que aparezca en la lista de direcciones, puede impedir que ese grupo aparezca en la GAL.</span><span class="sxs-lookup"><span data-stu-id="24211-148">For example, if you have a legal department group that you don't want to show up in the address list, you can stop that group from appearing in GAL.</span></span> <span data-ttu-id="24211-149">Ejecute el cmdlet Set-Unified Group para ocultar el grupo de la lista de direcciones de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="24211-149">Run the Set-Unified Group cmdlet to hide the group from address list like this:</span></span>
  
```
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a><span data-ttu-id="24211-150">Permitir que solo los usuarios internos envíen mensajes al grupo de Office 365</span><span class="sxs-lookup"><span data-stu-id="24211-150">Allow only internal users to send message to Office 365 group</span></span>
<span data-ttu-id="24211-151"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="24211-151"><a name="BKMK_CreateClassification"> </a></span></span>

<span data-ttu-id="24211-152">Si no desea que los usuarios de otras organizaciones envíen correo electrónico a un grupo de Office 365, puede cambiar la configuración de ese grupo.</span><span class="sxs-lookup"><span data-stu-id="24211-152">If you don't want users from other organization to send email to an Office 365 group, you can change the settings for that group.</span></span> <span data-ttu-id="24211-153">Permitirá que solo los usuarios internos envíen un correo electrónico a su grupo.</span><span class="sxs-lookup"><span data-stu-id="24211-153">It will allow only internal users to send an email to your group.</span></span> <span data-ttu-id="24211-154">Si un usuario externo intenta enviar un mensaje a ese grupo, se rechazará.</span><span class="sxs-lookup"><span data-stu-id="24211-154">If external user try to send message to that group they will be rejected.</span></span>
  
<span data-ttu-id="24211-155">Ejecute el cmdlet Set-UnifiedGroup para actualizar esta configuración, como se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="24211-155">Run the Set-UnifiedGroup cmdlet to update this setting, like this:</span></span>

```
Set-UnifiedGroup -Identity "Internal senders only" -RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-the-office-365-groups"></a><span data-ttu-id="24211-156">Agregar sugerencias de correo a los grupos de Office 365</span><span class="sxs-lookup"><span data-stu-id="24211-156">Add MailTips to the Office 365 Groups</span></span>
<span data-ttu-id="24211-157"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="24211-157"><a name="BKMK_CreateClassification"> </a></span></span>

<span data-ttu-id="24211-158">Cuando un remitente intenta enviar un correo electrónico a un grupo de Office 365, se le puede mostrar una sugerencia de correo electrónico.</span><span class="sxs-lookup"><span data-stu-id="24211-158">Whenever a sender tries to send an email to an Office 365 group, a MailTip can be shown to them.</span></span>
  
<span data-ttu-id="24211-159">Ejecute el cmdlet Set-Unified Group para agregar una sugerencia de correo al Grupo:</span><span class="sxs-lookup"><span data-stu-id="24211-159">Run the Set-Unified Group cmdlet to add a mailTip to the group:</span></span>

```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

<span data-ttu-id="24211-160">Además de la sugerencia de correo, también puede establecer MailTipTranslations, que especifica los idiomas adicionales para la sugerencia de correo.</span><span class="sxs-lookup"><span data-stu-id="24211-160">Along with MailTip, you can also set MailTipTranslations, which specifies additional languages for the MailTip.</span></span> <span data-ttu-id="24211-161">Suponga que quiere tener la traducción al español y, a continuación, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="24211-161">Suppose you want to have the Spanish translation, then run the following command:</span></span>
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-display-name-of-the-office-365-group"></a><span data-ttu-id="24211-162">Cambiar el nombre para mostrar del grupo de Office 365</span><span class="sxs-lookup"><span data-stu-id="24211-162">Change Display name of the Office 365 group</span></span>

<span data-ttu-id="24211-163">Nombre para mostrar especifica el nombre del grupo de Office 365.</span><span class="sxs-lookup"><span data-stu-id="24211-163">Display name specifies the name of the Office 365 group.</span></span> <span data-ttu-id="24211-164">Puede ver este nombre en su centro de administración de Exchange o en el centro de administración de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="24211-164">You can see this name in your exchange admin center or Microsoft 365 admin center.</span></span> <span data-ttu-id="24211-165">Puede editar el nombre para mostrar del grupo o asignar un nombre para mostrar a un grupo existente de Office 365 mediante la ejecución del comando set-UnifiedGroup:</span><span class="sxs-lookup"><span data-stu-id="24211-165">You can edit the display name of the group or assign a display name to an existing Office 365 group by running the Set-UnifiedGroup command:</span></span>

```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a><span data-ttu-id="24211-166">Cambiar la configuración predeterminada de Office 365 Groups para Outlook a Public o Private</span><span class="sxs-lookup"><span data-stu-id="24211-166">Change the default setting of Office 365 Groups for Outlook to Public or Private</span></span>
<span data-ttu-id="24211-167"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="24211-167"><a name="BKMK_CreateClassification"> </a></span></span>

<span data-ttu-id="24211-168">Office 365 grupos en Outlook se crean como privados de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="24211-168">Office 365 Groups in Outlook are created as Private by default.</span></span> <span data-ttu-id="24211-169">Si su organización desea que los grupos de Office 365 se creen como públicos de forma predeterminada (o volver a privado), use esta sintaxis de cmdlet de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="24211-169">If your organization wants Office 365 Groups to be created as Public by default (or back to Private), use this PowerShell cmdlet syntax:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
<span data-ttu-id="24211-170">Para establecer en privado:</span><span class="sxs-lookup"><span data-stu-id="24211-170">To set to Private:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
<span data-ttu-id="24211-171">Para comprobar la configuración:</span><span class="sxs-lookup"><span data-stu-id="24211-171">To verify the setting:</span></span> 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
<span data-ttu-id="24211-172">Para obtener más información, consulte [set-organizationconfig](https://docs.microsoft.com/powershell/module/exchange/set-organizationconfig) y [Get-organizationconfig](https://docs.microsoft.com/powershell/module/exchange/Get-OrganizationConfig).</span><span class="sxs-lookup"><span data-stu-id="24211-172">To learn more, see [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/set-organizationconfig) and [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/Get-OrganizationConfig).</span></span>
  
## <a name="office-365-groups-cmdlets"></a><span data-ttu-id="24211-173">Cmdlets de grupos de Office 365</span><span class="sxs-lookup"><span data-stu-id="24211-173">Office 365 Groups cmdlets</span></span>

<span data-ttu-id="24211-174">Los siguientes cmdlets se pueden usar con los grupos de Office 365.</span><span class="sxs-lookup"><span data-stu-id="24211-174">The following cmdlets can be used with Office 365 Groups.</span></span>
  
|<span data-ttu-id="24211-175">**Nombre de cmdlet**</span><span class="sxs-lookup"><span data-stu-id="24211-175">**Cmdlet name**</span></span>|<span data-ttu-id="24211-176">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="24211-176">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="24211-177">Get-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="24211-177">Get-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |<span data-ttu-id="24211-178">Use este cmdlet para buscar grupos existentes de Office 365 y para ver las propiedades del objeto de grupo.</span><span class="sxs-lookup"><span data-stu-id="24211-178">Use this cmdlet to look up existing Office 365 Groups, and to view properties of the group object</span></span>  <br/> |
|[<span data-ttu-id="24211-179">Set-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="24211-179">Set-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |<span data-ttu-id="24211-180">Actualizar las propiedades de un grupo específico de Office 365</span><span class="sxs-lookup"><span data-stu-id="24211-180">Update the properties of a specific Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="24211-181">New-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="24211-181">New-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |<span data-ttu-id="24211-182">Cree un nuevo grupo de Office 365.</span><span class="sxs-lookup"><span data-stu-id="24211-182">Create a new Office 365 group.</span></span> <span data-ttu-id="24211-183">Este cmdlet proporciona un conjunto mínimo de parámetros para establecer los valores de las propiedades extendidas usando Set-UnifiedGroup después de crear el nuevo grupo.</span><span class="sxs-lookup"><span data-stu-id="24211-183">This cmdlet provides a minimal set of parameters, for setting values for extended properties use Set-UnifiedGroup after creating the new group</span></span>  <br/> |
|[<span data-ttu-id="24211-184">Remove-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="24211-184">Remove-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |<span data-ttu-id="24211-185">Eliminar un grupo existente de Office 365</span><span class="sxs-lookup"><span data-stu-id="24211-185">Delete an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="24211-186">Get-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="24211-186">Get-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |<span data-ttu-id="24211-187">Recuperar la información de pertenencia y propietario de un grupo de Office 365</span><span class="sxs-lookup"><span data-stu-id="24211-187">Retrieve membership and owner information for an Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="24211-188">Add-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="24211-188">Add-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |<span data-ttu-id="24211-189">Agregar cientos o miles de usuarios, o propietarios nuevos, a un grupo existente de Office 365</span><span class="sxs-lookup"><span data-stu-id="24211-189">Add hundred or thousands of users, or new owners, to an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="24211-190">Remove-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="24211-190">Remove-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |<span data-ttu-id="24211-191">Quitar propietarios y miembros de un grupo existente de Office 365</span><span class="sxs-lookup"><span data-stu-id="24211-191">Remove owners and members from an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="24211-192">Get-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="24211-192">Get-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |<span data-ttu-id="24211-193">Se usa para ver información sobre la foto de usuario asociada a una cuenta.</span><span class="sxs-lookup"><span data-stu-id="24211-193">Used to view information about the user photo associated with an account.</span></span> <span data-ttu-id="24211-194">Las fotos de los usuarios se almacenan en Active Directory</span><span class="sxs-lookup"><span data-stu-id="24211-194">User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="24211-195">Set-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="24211-195">Set-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |<span data-ttu-id="24211-196">Se usa para asociar una foto de usuario con una cuenta.</span><span class="sxs-lookup"><span data-stu-id="24211-196">Used to associate a user photo with an account.</span></span> <span data-ttu-id="24211-197">Las fotos de los usuarios se almacenan en Active Directory</span><span class="sxs-lookup"><span data-stu-id="24211-197">User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="24211-198">Remove-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="24211-198">Remove-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |<span data-ttu-id="24211-199">Quitar la foto de un grupo de Office 365</span><span class="sxs-lookup"><span data-stu-id="24211-199">Remove the photo for an Office 365 group</span></span>  <br/> |

## <a name="related-topics"></a><span data-ttu-id="24211-200">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="24211-200">Related topics</span></span>

[<span data-ttu-id="24211-201">Actualizar listas de distribución a grupos de Office 365</span><span class="sxs-lookup"><span data-stu-id="24211-201">Upgrade distribution lists to Office 365 Groups</span></span>](https://docs.microsoft.com/office365/admin/manage/upgrade-distribution-lists)

[<span data-ttu-id="24211-202">Administrar quién puede crear grupos de Office 365</span><span class="sxs-lookup"><span data-stu-id="24211-202">Manage who can create Office 365 Groups</span></span>](https://docs.microsoft.com/office365/admin/create-groups/manage-creation-of-groups)

[<span data-ttu-id="24211-203">Administrar el acceso de invitados a los grupos de Office 365</span><span class="sxs-lookup"><span data-stu-id="24211-203">Manage guest access to Office 365 Groups</span></span>](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[<span data-ttu-id="24211-204">Cambiar la pertenencia al grupo estático a dinámico</span><span class="sxs-lookup"><span data-stu-id="24211-204">Change static group membership to dynamic in</span></span>](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-change-type)
