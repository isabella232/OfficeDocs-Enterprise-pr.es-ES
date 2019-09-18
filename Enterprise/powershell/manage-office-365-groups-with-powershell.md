---
title: Administrar grupos de Office 365 con PowerShell
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BSA160
- BCS160
ms.assetid: aeb669aa-1770-4537-9de2-a82ac11b0540
description: Obtenga información sobre cómo realizar tareas de administración comunes para los grupos de Office 365 en Microsoft PowerShell.
ms.openlocfilehash: 7e07041516acd3c2038dd92b464073279c49d1a6
ms.sourcegitcommit: d388c76d25ca67f240db97f7bfc90f0991b0e7f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2019
ms.locfileid: "37017348"
---
# <a name="manage-office-365-groups-with-powershell"></a><span data-ttu-id="4e2eb-103">Administrar grupos de Office 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="4e2eb-103">Manage Office 365 Groups with PowerShell</span></span>

 <span data-ttu-id="4e2eb-104">*Última actualización el 18 de abril de 2018*</span><span class="sxs-lookup"><span data-stu-id="4e2eb-104">*Last updated 18 April, 2018*</span></span> 
  
<span data-ttu-id="4e2eb-105">En este artículo se describen los pasos para realizar tareas de administración comunes para los grupos de Microsoft PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-105">This article provides the steps for doing common management tasks for Groups in Microsoft PowerShell.</span></span> <span data-ttu-id="4e2eb-106">También muestra los cmdlets de PowerShell para grupos.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-106">It also lists the PowerShell cmdlets for Groups.</span></span> <span data-ttu-id="4e2eb-107">Para obtener información sobre la administración de sitios de SharePoint, vea [administrar sitios de SharePoint Online con PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).</span><span class="sxs-lookup"><span data-stu-id="4e2eb-107">For info about managing SharePoint sites, see [Manage SharePoint Online sites using PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).</span></span>

## <a name="link-to-your-office-365-groups-usage-guidelines"></a><span data-ttu-id="4e2eb-108">Vínculo a las instrucciones de uso de los grupos de Office 365</span><span class="sxs-lookup"><span data-stu-id="4e2eb-108">Link to your Office 365 Groups usage guidelines</span></span>
<span data-ttu-id="4e2eb-109"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="4e2eb-109"></span></span>

<span data-ttu-id="4e2eb-110">Cuando los usuarios [creen o editen un grupo en Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), podrá mostrarles un vínculo a las instrucciones de uso de su organización.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-110">When users [create or edit a group in Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), you can show them a link to your organization's usage guidelines.</span></span> <span data-ttu-id="4e2eb-111">Por ejemplo, si necesita agregar un prefijo o un sufijo específico a un nombre de grupo.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-111">For example, if you require a specific prefix or suffix to be added to a group name.</span></span>
  
<span data-ttu-id="4e2eb-112">Use Azure Active Directory PowerShell para apuntar a los usuarios a las directrices de uso de su organización para los grupos de Office 365.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-112">Use the Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups.</span></span> <span data-ttu-id="4e2eb-113">Consulte [Azure Active Directory cmdlets para configurar las opciones de grupo](https://go.microsoft.com/fwlink/?LinkID=827484) y siga los pasos que se indican en el vínculo **crear configuración a nivel de directorio** para definir el hipervínculo de la instrucción de uso.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-113">Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the usage guideline hyperlink.</span></span> <span data-ttu-id="4e2eb-114">Una vez que se haya ejecutado el cmdlet de AAD, el usuario verá el vínculo a las directrices al crear o editar un grupo en Outlook.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-114">Once you run the AAD cmdlet, user's will see the link to your guidelines when they create or edit a group in Outlook.</span></span> 
  
![Crear un nuevo grupo con el vínculo de instrucciones de uso](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![Haga clic en instrucciones de uso de grupos para ver las directrices de grupos de Office 365](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
## <a name="allow-users-to-send-as-the-office-365-group"></a><span data-ttu-id="4e2eb-117">Permitir que los usuarios envíen como el grupo de Office 365</span><span class="sxs-lookup"><span data-stu-id="4e2eb-117">Allow users to Send as the Office 365 Group</span></span>
<span data-ttu-id="4e2eb-118"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="4e2eb-118"></span></span>
  
<span data-ttu-id="4e2eb-119">Si desea habilitar los grupos de Office 365 en "enviar como", use los cmdlets [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission) y [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient) para configurarlos.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-119">If you want to enable your Office 365 groups to "Send As", use the [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission) and the [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient) cmdlets to configure this.</span></span> <span data-ttu-id="4e2eb-120">Una vez habilitada esta opción, los usuarios de grupo de Office 365 pueden usar Outlook o Outlook en la web para enviar y responder correo electrónico como el grupo de Office 365.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-120">Once you enable this setting, Office 365 group users can use Outlook or Outlook on the web to send and reply to email as the Office 365 group.</span></span> <span data-ttu-id="4e2eb-121">Los usuarios pueden ir al grupo, crear un nuevo correo electrónico y cambiar el campo "enviar como" por la dirección de correo electrónico del grupo.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-121">Users can go to the group, create a new email, and change the "Send As" field to the group's email address.</span></span> 

<span data-ttu-id="4e2eb-122">([También puede hacerlo en el centro de administración de Exchange](https://docs.microsoft.com/en-us/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group)).</span><span class="sxs-lookup"><span data-stu-id="4e2eb-122">([You can also do this in the Exchange Admin Center](https://docs.microsoft.com/en-us/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group).)</span></span>
  
<span data-ttu-id="4e2eb-123">Use el siguiente script, reemplazando \* \<GroupAlias\> \* por el alias del grupo que desea actualizar y \* \<UserAlias\> \* con el alias del usuario al que desea conceder permssions.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-123">Use the following script, replacing *\<GroupAlias\>* with the alias of the group that you want to update, and *\<UserAlias\>* with the alias of the user to whom you want to grant permssions.</span></span> <span data-ttu-id="4e2eb-124">[Conéctese a Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) para ejecutar este script.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-124">[Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) to run this script.</span></span>

```PowerShell
$groupAlias = "<GroupAlias>"

$userAlias = "<UserAlias>"


$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

<span data-ttu-id="4e2eb-125">Una vez que se ejecuta el cmdlet, los usuarios pueden ir a Outlook o Outlook en la web para enviarlos como grupo, agregando la dirección de correo electrónico del grupo al campo **de** .</span><span class="sxs-lookup"><span data-stu-id="4e2eb-125">Once the cmdlet is executed, users can go to Outlook or Outlook on the web to send as the group, by adding the group email address to the **From** field.</span></span> 

## <a name="create-classifications-for-office-groups-in-your-organization"></a><span data-ttu-id="4e2eb-126">Crear clasificaciones para los grupos de Office en su organización</span><span class="sxs-lookup"><span data-stu-id="4e2eb-126">Create classifications for Office groups in your organization</span></span>

<span data-ttu-id="4e2eb-127">Puede crear clasificaciones que los usuarios de la organización pueden establecer al crear un grupo de Office 365.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-127">You can create classifications that the users in your organization can set when they create an Office 365 group.</span></span> <span data-ttu-id="4e2eb-128">Por ejemplo, puede permitir que los usuarios establezcan "Standard", "Secret" y "Top Secret" en los grupos que crean.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-128">For example, you can allow users to set "Standard", "Secret", and "Top Secret" on groups they create.</span></span> <span data-ttu-id="4e2eb-129">Las clasificaciones de grupo no se establecen de forma predeterminada y es necesario crearlas para que los usuarios las configuren.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-129">Group classifications aren't set by default and you need to create it in order for your users to set it.</span></span> <span data-ttu-id="4e2eb-130">Use Azure Active Directory PowerShell para dirigir a los usuarios a las instrucciones de uso de la organización para los grupos de Office 365.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-130">Use Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups.</span></span>
  
<span data-ttu-id="4e2eb-131">Consulte los [cmdlets de Azure Active Directory para configurar las opciones de grupo](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) y siga los pasos descritos en la **opción crear configuración a nivel de directorio** para definir la clasificación de los grupos de Office 365.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-131">Check out [Azure Active Directory cmdlets for configuring group settings](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) and follow the steps in the **Create settings at the directory level** to define the classification for Office 365 groups.</span></span> 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

<span data-ttu-id="4e2eb-132">Para asociar una descripción a cada clasificación, puede usar el atributo Settings *ClassificationDescriptions* para definirla.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-132">In order to associate a description to each classification you can use the settings attribute  *ClassificationDescriptions* to define.</span></span>
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

<span data-ttu-id="4e2eb-133">donde clasificación coincide con las cadenas de ClassificationList.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-133">where Classification matches the strings in the ClassificationList.</span></span>

<span data-ttu-id="4e2eb-134">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="4e2eb-134">Example:</span></span>
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

<span data-ttu-id="4e2eb-135">Después de ejecutar el cmdlet de Azure Active Directory anterior para establecer la clasificación, ejecute el cmdlet [set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) si desea establecer la clasificación para un grupo específico.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-135">After you run the above Azure Active Directory cmdlet to set your classification, run the [Set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) cmdlet if you want to set the classification for a specific group.</span></span> 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

<span data-ttu-id="4e2eb-136">O bien, cree un nuevo grupo con una clasificación.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-136">Or create a new group with a classification.</span></span>
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

<span data-ttu-id="4e2eb-137">Vea [usar PowerShell con Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) y [Conéctese a Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) para obtener más información sobre el uso de Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-137">Check out [Using PowerShell with Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) and [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) for more details on using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="4e2eb-138">Una vez habilitada esta configuración, el propietario del grupo podrá elegir una clasificación en el menú desplegable de Outlook en la web y en Outlook, y guardarla desde la página **Editar** grupo.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-138">Once these settings are enabled, the group owner will be able to choose a classification from the drop down menu in Outlook on the Web and Outlook, and save it from the **Edit** group page.</span></span> 
  
![Elegir la clasificación de grupo de Office 365](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
## <a name="hide-office-365-groups-from-gal"></a><span data-ttu-id="4e2eb-140">Ocultar grupos de Office 365 desde GAL</span><span class="sxs-lookup"><span data-stu-id="4e2eb-140">Hide Office 365 Groups from GAL</span></span>
<span data-ttu-id="4e2eb-141"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="4e2eb-141"></span></span>

<span data-ttu-id="4e2eb-142">Puede especificar si un grupo de Office 365 aparece en la lista global de direcciones (GAL) y en otras listas de la organización.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-142">You can specify whether a Office 365 group appears in the global address list (GAL) and other lists in your organization.</span></span> <span data-ttu-id="4e2eb-143">Por ejemplo, si tiene un grupo de departamento legal que no desea que aparezca en la lista de direcciones, puede impedir que ese grupo aparezca en la GAL.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-143">For example, if you have a legal department group that you don't want to show up in the address list, you can stop that group from appearing in GAL.</span></span> <span data-ttu-id="4e2eb-144">Ejecute el cmdlet Set-Unified Group para ocultar el grupo de la lista de direcciones de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="4e2eb-144">Run the Set-Unified Group cmdlet to hide the group from address list like this:</span></span>
  
```
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a><span data-ttu-id="4e2eb-145">Permitir que solo los usuarios internos envíen mensajes al grupo de Office 365</span><span class="sxs-lookup"><span data-stu-id="4e2eb-145">Allow only internal users to send message to Office 365 group</span></span>
<span data-ttu-id="4e2eb-146"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="4e2eb-146"></span></span>

<span data-ttu-id="4e2eb-147">Si no quiere que los usuarios de otras organizaciones envíen correo electrónico a un grupo de Office 365, puede cambiar la configuración de ese grupo.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-147">If you don't want users from other organization to send email to a Office 365 group, you can change the settings for that group.</span></span> <span data-ttu-id="4e2eb-148">Permitirá que solo los usuarios internos envíen un correo electrónico a su grupo.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-148">It will allow only internal users to send an email to your group.</span></span> <span data-ttu-id="4e2eb-149">Si un usuario externo intenta enviar un mensaje a ese grupo, se rechazará.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-149">If external user try to send message to that group they will be rejected.</span></span>
  
<span data-ttu-id="4e2eb-150">Ejecute el cmdlet Set-UnifiedGroup para actualizar esta configuración, como se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="4e2eb-150">Run the Set-UnifiedGroup cmdlet to update this setting, like this:</span></span>

```
Set-UnifiedGroup -Identity "Internal senders only" -RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-the-office-365-groups"></a><span data-ttu-id="4e2eb-151">Agregar sugerencias de correo a los grupos de Office 365</span><span class="sxs-lookup"><span data-stu-id="4e2eb-151">Add MailTips to the Office 365 Groups</span></span>
<span data-ttu-id="4e2eb-152"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="4e2eb-152"></span></span>

<span data-ttu-id="4e2eb-153">Cuando un remitente intenta enviar un correo electrónico a un grupo de Office 365, se le puede mostrar una sugerencia de correo electrónico.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-153">Whenever a sender tries to send an email to an Office 365 group, a MailTip can be shown to them.</span></span>
  
<span data-ttu-id="4e2eb-154">Ejecute el cmdlet Set-Unified Group para agregar una sugerencia de correo al Grupo:</span><span class="sxs-lookup"><span data-stu-id="4e2eb-154">Run the Set-Unified Group cmdlet to add a mailTip to the group:</span></span>

```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

<span data-ttu-id="4e2eb-155">Además de la sugerencia de correo, también puede establecer MailTipTranslations, que especifica los idiomas adicionales para la sugerencia de correo.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-155">Along with MailTip, you can also set MailTipTranslations, which specifies additional languages for the MailTip.</span></span> <span data-ttu-id="4e2eb-156">Suponga que quiere tener la traducción al español y, a continuación, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="4e2eb-156">Suppose you want to have the Spanish translation, then run the following command:</span></span>
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-display-name-of-the-office-365-group"></a><span data-ttu-id="4e2eb-157">Cambiar el nombre para mostrar del grupo de Office 365</span><span class="sxs-lookup"><span data-stu-id="4e2eb-157">Change Display name of the Office 365 group</span></span>

<span data-ttu-id="4e2eb-158">Nombre para mostrar especifica el nombre del grupo de Office 365.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-158">Display name specifies the name of the Office 365 group.</span></span> <span data-ttu-id="4e2eb-159">Puede ver este nombre en su centro de administración de Exchange o en el portal de administración de Office 365.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-159">You can see this name in your exchange admin center or Office 365 admin portal.</span></span> <span data-ttu-id="4e2eb-160">Puede editar el nombre para mostrar del grupo o asignar un nombre para mostrar a un grupo existente de Office 365 mediante la ejecución del comando set-UnifiedGroup:</span><span class="sxs-lookup"><span data-stu-id="4e2eb-160">You can edit the display name of the group or assign a display name to an existing Office 365 group by running the Set-UnifiedGroup command:</span></span>

```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a><span data-ttu-id="4e2eb-161">Cambiar la configuración predeterminada de Office 365 Groups para Outlook a Public o Private</span><span class="sxs-lookup"><span data-stu-id="4e2eb-161">Change the default setting of Office 365 Groups for Outlook to Public or Private</span></span>
<span data-ttu-id="4e2eb-162"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="4e2eb-162"></span></span>

<span data-ttu-id="4e2eb-163">Office 365 grupos en Outlook se crean como privados de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-163">Office 365 Groups in Outlook are created as Private by default.</span></span> <span data-ttu-id="4e2eb-164">Si su organización desea que los grupos de Office 365 se creen como públicos de forma predeterminada (o volver a privado), use esta sintaxis de cmdlet de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="4e2eb-164">If your organization wants Office 365 Groups to be created as Public by default (or back to Private), use this PowerShell cmdlet syntax:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
<span data-ttu-id="4e2eb-165">Para establecer en privado:</span><span class="sxs-lookup"><span data-stu-id="4e2eb-165">To set to Private:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
<span data-ttu-id="4e2eb-166">Para comprobar la configuración:</span><span class="sxs-lookup"><span data-stu-id="4e2eb-166">To verify the setting:</span></span> 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
<span data-ttu-id="4e2eb-167">Para obtener más información, consulte [set-organizationconfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig) y [Get-organizationconfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig).</span><span class="sxs-lookup"><span data-stu-id="4e2eb-167">To learn more, see [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig) and [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig).</span></span>
  
## <a name="office-365-groups-cmdlets"></a><span data-ttu-id="4e2eb-168">Cmdlets de grupos de Office 365</span><span class="sxs-lookup"><span data-stu-id="4e2eb-168">Office 365 Groups cmdlets</span></span>

<span data-ttu-id="4e2eb-169">Los siguientes cmdlets se pueden usar con los grupos de Office 365.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-169">The following cmdlets can be used with Office 365 Groups.</span></span>
  
|<span data-ttu-id="4e2eb-170">**Nombre de cmdlet**</span><span class="sxs-lookup"><span data-stu-id="4e2eb-170">**Cmdlet name**</span></span>|<span data-ttu-id="4e2eb-171">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="4e2eb-171">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="4e2eb-172">Get-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="4e2eb-172">Get-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |<span data-ttu-id="4e2eb-173">Use este cmdlet para buscar grupos existentes de Office 365 y para ver las propiedades del objeto de grupo.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-173">Use this cmdlet to look up existing Office 365 Groups, and to view properties of the group object</span></span>  <br/> |
|[<span data-ttu-id="4e2eb-174">Set-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="4e2eb-174">Set-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |<span data-ttu-id="4e2eb-175">Actualizar las propiedades de un grupo específico de Office 365</span><span class="sxs-lookup"><span data-stu-id="4e2eb-175">Update the properties of a specific Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="4e2eb-176">New-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="4e2eb-176">New-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |<span data-ttu-id="4e2eb-177">Cree un nuevo grupo de Office 365.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-177">Create a new Office 365 group.</span></span> <span data-ttu-id="4e2eb-178">Este cmdlet proporciona un conjunto mínimo de parámetros para establecer los valores de las propiedades extendidas usando Set-UnifiedGroup después de crear el nuevo grupo.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-178">This cmdlet provides a minimal set of parameters, for setting values for extended properties use Set-UnifiedGroup after creating the new group</span></span>  <br/> |
|[<span data-ttu-id="4e2eb-179">Remove-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="4e2eb-179">Remove-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |<span data-ttu-id="4e2eb-180">Eliminar un grupo existente de Office 365</span><span class="sxs-lookup"><span data-stu-id="4e2eb-180">Delete an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="4e2eb-181">Get-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="4e2eb-181">Get-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |<span data-ttu-id="4e2eb-182">Recuperar la información de pertenencia y propietario de un grupo de Office 365</span><span class="sxs-lookup"><span data-stu-id="4e2eb-182">Retrieve membership and owner information for an Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="4e2eb-183">Add-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="4e2eb-183">Add-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |<span data-ttu-id="4e2eb-184">Agregar cientos o miles de usuarios, o propietarios nuevos, a un grupo existente de Office 365</span><span class="sxs-lookup"><span data-stu-id="4e2eb-184">Add hundred or thousands of users, or new owners, to an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="4e2eb-185">Remove-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="4e2eb-185">Remove-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |<span data-ttu-id="4e2eb-186">Quitar propietarios y miembros de un grupo existente de Office 365</span><span class="sxs-lookup"><span data-stu-id="4e2eb-186">Remove owners and members from an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="4e2eb-187">Get-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="4e2eb-187">Get-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |<span data-ttu-id="4e2eb-188">Se usa para ver información sobre la foto de usuario asociada a una cuenta.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-188">Used to view information about the user photo associated with an account.</span></span> <span data-ttu-id="4e2eb-189">Las fotos de los usuarios se almacenan en Active Directory</span><span class="sxs-lookup"><span data-stu-id="4e2eb-189">User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="4e2eb-190">Set-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="4e2eb-190">Set-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |<span data-ttu-id="4e2eb-191">Se usa para asociar una foto de usuario con una cuenta.</span><span class="sxs-lookup"><span data-stu-id="4e2eb-191">Used to associate a user photo with an account.</span></span> <span data-ttu-id="4e2eb-192">Las fotos de los usuarios se almacenan en Active Directory</span><span class="sxs-lookup"><span data-stu-id="4e2eb-192">User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="4e2eb-193">Remove-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="4e2eb-193">Remove-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |<span data-ttu-id="4e2eb-194">Quitar la foto de un grupo de Office 365</span><span class="sxs-lookup"><span data-stu-id="4e2eb-194">Remove the photo for an Office 365 group</span></span>  <br/> |

## <a name="related-topics"></a><span data-ttu-id="4e2eb-195">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="4e2eb-195">Related topics</span></span>

[<span data-ttu-id="4e2eb-196">Actualizar listas de distribución a grupos de Office 365</span><span class="sxs-lookup"><span data-stu-id="4e2eb-196">Upgrade distribution lists to Office 365 Groups</span></span>](https://docs.microsoft.com/en-us/office365/admin/manage/upgrade-distribution-lists)

[<span data-ttu-id="4e2eb-197">Administrar quién puede crear grupos de Office 365</span><span class="sxs-lookup"><span data-stu-id="4e2eb-197">Manage who can create Office 365 Groups</span></span>](https://docs.microsoft.com/en-us/office365/admin/create-groups/manage-creation-of-groups)

[<span data-ttu-id="4e2eb-198">Administrar el acceso de invitados a los grupos de Office 365</span><span class="sxs-lookup"><span data-stu-id="4e2eb-198">Manage guest access to Office 365 Groups</span></span>](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[<span data-ttu-id="4e2eb-199">Cambiar la pertenencia al grupo estático a dinámico</span><span class="sxs-lookup"><span data-stu-id="4e2eb-199">Change static group membership to dynamic in</span></span>](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-change-type)
