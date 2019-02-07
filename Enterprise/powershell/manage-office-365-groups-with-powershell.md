---
title: Administrar grupos de Office 365 con PowerShell
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: Admin
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
description: Obtenga información sobre cómo realizar tareas comunes de administración de Office 365 grupos en PowerShell de Microsoft.
ms.openlocfilehash: 6d7841595315507b0b7f28f6b86f9349705f1d8b
ms.sourcegitcommit: 662d75796991bac4e959348ded4999008875422e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/06/2019
ms.locfileid: "29760062"
---
# <a name="manage-office-365-groups-with-powershell"></a><span data-ttu-id="90e1a-103">Administrar grupos de Office 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="90e1a-103">Manage Office 365 Groups with PowerShell</span></span>

 <span data-ttu-id="90e1a-104">*Última 18 de abril actualizados de 2018*</span><span class="sxs-lookup"><span data-stu-id="90e1a-104">*Last updated 18 April, 2018*</span></span> 
  
<span data-ttu-id="90e1a-p101">Este artículo proporciona los pasos para realizar tareas comunes de administración de grupos en PowerShell de Microsoft. También se enumeran los cmdlets de PowerShell para grupos. Para información sobre la administración de sitios de SharePoint, vea [sitios de administración de SharePoint Online mediante PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).</span><span class="sxs-lookup"><span data-stu-id="90e1a-p101">This article provides the steps for doing common management tasks for Groups in Microsoft PowerShell. It also lists the PowerShell cmdlets for Groups. For info about managing SharePoint sites, see [Manage SharePoint Online sites using PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).</span></span>

## <a name="link-to-your-office-365-groups-usage-guidelines"></a><span data-ttu-id="90e1a-108">Vínculo a las directrices de uso de grupos de Office 365</span><span class="sxs-lookup"><span data-stu-id="90e1a-108">Link to your Office 365 Groups usage guidelines</span></span>
<span data-ttu-id="90e1a-109"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="90e1a-109"></span></span>

<span data-ttu-id="90e1a-p102">Cuando los usuarios [crear o editar un grupo en Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), puede mostrarlos un vínculo a instrucciones sobre el uso de su organización. Por ejemplo, si se requiere un prefijo específico o sufijo que se agrega a un nombre de grupo.</span><span class="sxs-lookup"><span data-stu-id="90e1a-p102">When users [create or edit a group in Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), you can show them a link to your organization's usage guidelines. For example, if you require a specific prefix or suffix to be added to a group name.</span></span>
  
<span data-ttu-id="90e1a-p103">Use Azure Active Directory PowerShell para dirigir a los usuarios a instrucciones de uso de la organización para los grupos de Office 365. Desproteger [los cmdlets de Azure Active Directory para configurar las opciones de grupo](https://go.microsoft.com/fwlink/?LinkID=827484) y siga los pasos de la **configuración de crear en el nivel de directorio** para definir el hipervínculo de pauta de uso. Una vez que se ejecuta el cmdlet AAD, usuario verán el vínculo a sus instrucciones que indican cuándo crean o edición un grupo en Outlook.</span><span class="sxs-lookup"><span data-stu-id="90e1a-p103">Use the Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups. Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the usage guideline hyperlink. Once you run the AAD cmdlet, user's will see the link to your guidelines when they create or edit a group in Outlook.</span></span> 
  
![Crear un grupo nuevo con el vínculo de instrucciones de uso](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![Haga clic en directrices de uso de grupo para ver las organizaciones instrucciones de grupos de Office 365](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
## <a name="allow-users-to-send-as-the-office-365-group"></a><span data-ttu-id="90e1a-117">Permitir a los usuarios enviar como el grupo de Office 365</span><span class="sxs-lookup"><span data-stu-id="90e1a-117">Allow users to Send as the Office 365 Group</span></span>
<span data-ttu-id="90e1a-118"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="90e1a-118"></span></span>
  
<span data-ttu-id="90e1a-p104">Si desea habilitar a los grupos de Office 365 para "Enviar como", use el [Complemento RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission) y los cmdlets [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient) para realizar esta configuración. Una vez que se habilita a esta opción, los usuarios del grupo de Office 365 pueden usar Outlook o Outlook en la web para enviar y responder al correo electrónico como el grupo de Office 365. Los usuarios pueden ir al grupo, cree un correo electrónico nuevo y cambie el campo "Enviar como" a la dirección de correo electrónico del grupo.</span><span class="sxs-lookup"><span data-stu-id="90e1a-p104">If you want to enable your Office 365 groups to "Send As", use the [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission) and the [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient) cmdlets to configure this. Once you enable this setting, Office 365 group users can use Outlook or Outlook on the web to send and reply to email as the Office 365 group. Users can go to the group, create a new email, and change the "Send As" field to the group's email address.</span></span> 

<span data-ttu-id="90e1a-122">([También puede hacerlo en el centro de administración de Exchange](https://docs.microsoft.com/en-us/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group)).</span><span class="sxs-lookup"><span data-stu-id="90e1a-122">([You can also do this in the Exchange Admin Center](https://docs.microsoft.com/en-us/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group).)</span></span>
  
<span data-ttu-id="90e1a-p105">Use la siguiente secuencia de comandos, reemplazando \* \<GroupAlias\> \* con el alias del grupo que desea actualizar, y \* \<UserAlias\> \* con el alias del usuario a quien desea conceder permisos. [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) para ejecutar esta secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="90e1a-p105">Use the following script, replacing *\<GroupAlias\>* with the alias of the group that you want to update, and *\<UserAlias\>* with the alias of the user to whom you want to grant permssions. [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) to run this script.</span></span>

```PowerShell
$groupAlias = "<GroupAlias>"

$userAlias = "<UserAlias>"


$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

<span data-ttu-id="90e1a-125">Una vez que se ejecuta el cmdlet, pueden ir a los usuarios a Outlook o Outlook en la web para enviar como el grupo, mediante la adición de la dirección de correo electrónico de grupo para el campo **de** .</span><span class="sxs-lookup"><span data-stu-id="90e1a-125">Once the cmdlet is executed, users can go to Outlook or Outlook on the web to send as the group, by adding the group email address to the **From** field.</span></span> 

## <a name="create-classifications-for-office-groups-in-your-organization"></a><span data-ttu-id="90e1a-126">Crear clasificaciones para los grupos de Office en su organización</span><span class="sxs-lookup"><span data-stu-id="90e1a-126">Create classifications for Office groups in your organization</span></span>

<span data-ttu-id="90e1a-p106">Puede crear clasificaciones de que los usuarios de su organización pueden establecer al crear un grupo de Office 365. Por ejemplo, puede permitir a los usuarios establecer "Estándar", "Secret" y "Top Secret" en grupos que se crean. Clasificaciones de grupo no se establecen de forma predeterminada y debe crear en orden para los usuarios a establecerla. Use Windows Azure Active Directory PowerShell para dirigir a los usuarios a instrucciones de uso de la organización para los grupos de Office 365.</span><span class="sxs-lookup"><span data-stu-id="90e1a-p106">You can create classifications that the users in your organization can set when they create an Office 365 group. For example, you can allow users to set "Standard", "Secret", and "Top Secret" on groups they create. Group classifications aren't set by default and you need to create it in order for your users to set it. Use Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups.</span></span>
  
<span data-ttu-id="90e1a-131">Desproteger [los cmdlets de Azure Active Directory para configurar las opciones de grupo](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) y siga los pasos de la **configuración de crear en el nivel de directorio** para definir la clasificación de los grupos de Office 365.</span><span class="sxs-lookup"><span data-stu-id="90e1a-131">Check out [Azure Active Directory cmdlets for configuring group settings](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) and follow the steps in the **Create settings at the directory level** to define the classification for Office 365 groups.</span></span> 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

<span data-ttu-id="90e1a-132">Para asociar una descripción para cada clasificación que puede usar la configuración de atributo *ClassificationDescriptions* para definir.</span><span class="sxs-lookup"><span data-stu-id="90e1a-132">In order to associate a description to each classification you can use the settings attribute  *ClassificationDescriptions* to define.</span></span>
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

<span data-ttu-id="90e1a-133">donde clasificación coincide con las cadenas en el ClassificationList.</span><span class="sxs-lookup"><span data-stu-id="90e1a-133">where Classification matches the strings in the ClassificationList.</span></span>

<span data-ttu-id="90e1a-134">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="90e1a-134">Example:</span></span>
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

<span data-ttu-id="90e1a-135">Después de ejecutar el cmdlet anterior de Azure Active Directory para establecer la clasificación de su, ejecute el cmdlet [Set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) si desea establecer la clasificación de un grupo específico.</span><span class="sxs-lookup"><span data-stu-id="90e1a-135">After you run the above Azure Active Directory cmdlet to set your classification, run the [Set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) cmdlet if you want to set the classification for a specific group.</span></span> 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

<span data-ttu-id="90e1a-136">O bien, crear un grupo nuevo con una clasificación.</span><span class="sxs-lookup"><span data-stu-id="90e1a-136">Or create a new group with a classification.</span></span>
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

<span data-ttu-id="90e1a-137">Desproteger [Using PowerShell con Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) y [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) para obtener más detalles sobre el uso de Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="90e1a-137">Check out [Using PowerShell with Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) and [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) for more details on using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="90e1a-138">Una vez que estos valores están habilitados, el propietario del grupo podrán elegir una clasificación de la lista desplegable menú en Outlook en la Web y de Outlook y vuelva a guardarla desde la página de grupo **Editar** .</span><span class="sxs-lookup"><span data-stu-id="90e1a-138">Once these settings are enabled, the group owner will be able to choose a classification from the drop down menu in Outlook on the Web and Outlook, and save it from the **Edit** group page.</span></span> 
  
![Elija la clasificación de grupo de Office 365](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
## <a name="hide-office-365-groups-from-gal"></a><span data-ttu-id="90e1a-140">Ocultar los grupos de Office 365 desde la lista global de direcciones</span><span class="sxs-lookup"><span data-stu-id="90e1a-140">Hide Office 365 Groups from GAL</span></span>
<span data-ttu-id="90e1a-141"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="90e1a-141"></span></span>

<span data-ttu-id="90e1a-p107">Puede especificar si un grupo de Office 365 aparece en la lista global de direcciones (GAL) y otras listas de la organización. Por ejemplo, si tiene un grupo del departamento legal que no desea que aparezca en la lista de direcciones, puede detener ese grupo que no aparezca en la lista global de direcciones. Ejecute el cmdlet de grupo de Set-Unified para ocultar el grupo de la lista de direcciones como esta:</span><span class="sxs-lookup"><span data-stu-id="90e1a-p107">You can specify whether a Office 365 group appears in the global address list (GAL) and other lists in your organization. For example, if you have a legal department group that you don't want to show up in the address list, you can stop that group from appearing in GAL. Run the Set-Unified Group cmdlet to hide the group from address list like this:</span></span>
  
```
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a><span data-ttu-id="90e1a-145">Permitir que sólo los usuarios internos enviar el mensaje al grupo de Office 365</span><span class="sxs-lookup"><span data-stu-id="90e1a-145">Allow only internal users to send message to Office 365 group</span></span>
<span data-ttu-id="90e1a-146"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="90e1a-146"></span></span>

<span data-ttu-id="90e1a-p108">Si no desea que los usuarios de otra organización para enviar correo electrónico a un grupo de Office 365, puede cambiar la configuración de ese grupo. Le permitirá que sólo los usuarios internos enviar un correo electrónico a su grupo. Si un usuario externo intenta enviar mensaje a ese grupo serán rechazadas.</span><span class="sxs-lookup"><span data-stu-id="90e1a-p108">If you don't want users from other organization to send email to a Office 365 group, you can change the settings for that group. It will allow only internal users to send an email to your group. If external user try to send message to that group they will be rejected.</span></span>
  
<span data-ttu-id="90e1a-150">Ejecute el cmdlet Set-UnifiedGroup para actualizar esta configuración, como la siguiente:</span><span class="sxs-lookup"><span data-stu-id="90e1a-150">Run the Set-UnifiedGroup cmdlet to update this setting, like this:</span></span>

```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-the-office-365-groups"></a><span data-ttu-id="90e1a-151">Agregar sugerencias de correo electrónico a los grupos de Office 365</span><span class="sxs-lookup"><span data-stu-id="90e1a-151">Add MailTips to the Office 365 Groups</span></span>
<span data-ttu-id="90e1a-152"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="90e1a-152"></span></span>

<span data-ttu-id="90e1a-153">Cada vez que un remitente intenta enviar un correo electrónico a un grupo de Office 365, se puede mostrar una sugerencia de correo electrónico a ellos.</span><span class="sxs-lookup"><span data-stu-id="90e1a-153">Whenever a sender tries to send an email to an Office 365 group, a MailTip can be shown to them.</span></span>
  
<span data-ttu-id="90e1a-154">Ejecute el cmdlet de grupo de Set-Unified para agregar una sugerencia de correo electrónico para el grupo:</span><span class="sxs-lookup"><span data-stu-id="90e1a-154">Run the Set-Unified Group cmdlet to add a mailTip to the group:</span></span>

```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

<span data-ttu-id="90e1a-p109">Junto con la sugerencia de correo electrónico, también puede establecer MailTipTranslations, que especifica los idiomas adicionales para la sugerencia de correo electrónico. Suponga que desea tener la traducción al español, a continuación, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="90e1a-p109">Along with MailTip, you can also set MailTipTranslations, which specifies additional languages for the MailTip. Suppose you want to have the Spanish translation, then run the following command:</span></span>
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-display-name-of-the-office-365-group"></a><span data-ttu-id="90e1a-157">Cambiar el nombre para mostrar del grupo de Office 365</span><span class="sxs-lookup"><span data-stu-id="90e1a-157">Change Display name of the Office 365 group</span></span>

<span data-ttu-id="90e1a-p110">Nombre para mostrar especifica el nombre del grupo de Office 365. Puede ver este nombre en el centro de administración de exchange o el portal de administración de Office 365. Puede editar el nombre para mostrar del grupo o asignar un nombre para mostrar a un grupo existente de Office 365, ejecute el comando Set-UnifiedGroup:</span><span class="sxs-lookup"><span data-stu-id="90e1a-p110">Display name specifies the name of the Office 365 group. You can see this name in your exchange admin center or Office 365 admin portal. You can edit the display name of the group or assign a display name to an existing Office 365 group by running the Set-UnifiedGroup command:</span></span>

```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a><span data-ttu-id="90e1a-161">Cambie la configuración predeterminada de Office 365 grupos para Outlook al público o privado</span><span class="sxs-lookup"><span data-stu-id="90e1a-161">Change the default setting of Office 365 Groups for Outlook to Public or Private</span></span>
<span data-ttu-id="90e1a-162"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="90e1a-162"></span></span>

<span data-ttu-id="90e1a-p111">Office 365 se crean grupos en Outlook como privadas de forma predeterminada. Si su organización desea que Office 365 grupos que se creará como Public de forma predeterminada (o a la privada), use esta sintaxis de cmdlet de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="90e1a-p111">Office 365 Groups in Outlook are created as Private by default. If your organization wants Office 365 Groups to be created as Public by default (or back to Private), use this PowerShell cmdlet syntax:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
<span data-ttu-id="90e1a-165">Para establecer Private:</span><span class="sxs-lookup"><span data-stu-id="90e1a-165">To set to Private:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
<span data-ttu-id="90e1a-166">Para comprobar la configuración:</span><span class="sxs-lookup"><span data-stu-id="90e1a-166">To verify the setting:</span></span> 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
<span data-ttu-id="90e1a-167">Para obtener más información, vea [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig) y [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig).</span><span class="sxs-lookup"><span data-stu-id="90e1a-167">To learn more, see [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig) and [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig).</span></span>
  
## <a name="office-365-groups-cmdlets"></a><span data-ttu-id="90e1a-168">Cmdlets de grupos de Office 365</span><span class="sxs-lookup"><span data-stu-id="90e1a-168">Office 365 Groups cmdlets</span></span>

<span data-ttu-id="90e1a-169">Los cmdlets siguientes pueden usarse con Office 365 grupos.</span><span class="sxs-lookup"><span data-stu-id="90e1a-169">The following cmdlets can be used with Office 365 Groups.</span></span>
  
|<span data-ttu-id="90e1a-170">**Nombre de cmdlet**</span><span class="sxs-lookup"><span data-stu-id="90e1a-170">**Cmdlet name**</span></span>|<span data-ttu-id="90e1a-171">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="90e1a-171">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="90e1a-172">Get-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="90e1a-172">Get-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |<span data-ttu-id="90e1a-173">Use este cmdlet para buscar los grupos existentes de Office 365 y para ver las propiedades del objeto de grupo</span><span class="sxs-lookup"><span data-stu-id="90e1a-173">Use this cmdlet to look up existing Office 365 Groups, and to view properties of the group object</span></span>  <br/> |
|[<span data-ttu-id="90e1a-174">Set-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="90e1a-174">Set-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |<span data-ttu-id="90e1a-175">Actualizar las propiedades de un determinado grupo de Office 365</span><span class="sxs-lookup"><span data-stu-id="90e1a-175">Update the properties of a specific Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="90e1a-176">New-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="90e1a-176">New-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |<span data-ttu-id="90e1a-p112">Crear un nuevo grupo de Office 365. Este cmdlet proporciona un conjunto mínimo de parámetros, para la configuración de los valores de las propiedades extendidas usar Set-UnifiedGroup después de crear el nuevo grupo</span><span class="sxs-lookup"><span data-stu-id="90e1a-p112">Create a new Office 365 group. This cmdlet provides a minimal set of parameters, for setting values for extended properties use Set-UnifiedGroup after creating the new group</span></span>  <br/> |
|[<span data-ttu-id="90e1a-179">Remove-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="90e1a-179">Remove-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |<span data-ttu-id="90e1a-180">Eliminar un grupo de 365 existente de Office</span><span class="sxs-lookup"><span data-stu-id="90e1a-180">Delete an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="90e1a-181">Get-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="90e1a-181">Get-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |<span data-ttu-id="90e1a-182">Recuperar información de pertenencia y el propietario de un grupo de Office 365</span><span class="sxs-lookup"><span data-stu-id="90e1a-182">Retrieve membership and owner information for an Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="90e1a-183">Add-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="90e1a-183">Add-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |<span data-ttu-id="90e1a-184">Agregar cientos o miles de usuarios o los propietarios de nuevo, a un grupo de 365 existente de Office</span><span class="sxs-lookup"><span data-stu-id="90e1a-184">Add hundred or thousands of users, or new owners, to an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="90e1a-185">Remove-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="90e1a-185">Remove-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |<span data-ttu-id="90e1a-186">Quitar los propietarios y los miembros de un grupo de 365 existente de Office</span><span class="sxs-lookup"><span data-stu-id="90e1a-186">Remove owners and members from an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="90e1a-187">Get-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="90e1a-187">Get-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |<span data-ttu-id="90e1a-p113">Se usa para ver información acerca de la foto de usuario asociada con una cuenta. Fotografías de usuario se almacenan en Active Directory</span><span class="sxs-lookup"><span data-stu-id="90e1a-p113">Used to view information about the user photo associated with an account. User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="90e1a-190">Set-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="90e1a-190">Set-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |<span data-ttu-id="90e1a-p114">Se usa para asociar una foto de usuario con una cuenta. Fotografías de usuario se almacenan en Active Directory</span><span class="sxs-lookup"><span data-stu-id="90e1a-p114">Used to associate a user photo with an account. User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="90e1a-193">Remove-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="90e1a-193">Remove-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |<span data-ttu-id="90e1a-194">Quitar la foto para un grupo de Office 365</span><span class="sxs-lookup"><span data-stu-id="90e1a-194">Remove the photo for an Office 365 group</span></span>  <br/> |

## <a name="related-topics"></a><span data-ttu-id="90e1a-195">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="90e1a-195">Related topics</span></span>

[<span data-ttu-id="90e1a-196">Listas de distribución de actualización a los grupos de Office 365</span><span class="sxs-lookup"><span data-stu-id="90e1a-196">Upgrade distribution lists to Office 365 Groups</span></span>](https://docs.microsoft.com/en-us/office365/admin/manage/upgrade-distribution-lists)

[<span data-ttu-id="90e1a-197">Administrar quién puede crear grupos de Office 365</span><span class="sxs-lookup"><span data-stu-id="90e1a-197">Manage who can create Office 365 Groups</span></span>](https://docs.microsoft.com/en-us/office365/admin/create-groups/manage-creation-of-groups)

[<span data-ttu-id="90e1a-198">Administrar el acceso de invitados a Grupos de Office 365</span><span class="sxs-lookup"><span data-stu-id="90e1a-198">Manage guest access to Office 365 Groups</span></span>](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[<span data-ttu-id="90e1a-199">Cambiar la pertenencia al grupo estático a dinámico en</span><span class="sxs-lookup"><span data-stu-id="90e1a-199">Change static group membership to dynamic in</span></span>](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-change-type)
