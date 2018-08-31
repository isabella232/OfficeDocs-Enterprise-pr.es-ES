---
title: Administrar grupos de Office 365 con PowerShell
ms.author: dianef
author: dianef77
manager: scotv
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MOE150
- MED150
- MBS150
- BSA160
- BCS160
ms.assetid: aeb669aa-1770-4537-9de2-a82ac11b0540
description: Última 18 de abril actualizados de 2018
ms.openlocfilehash: 8def3b304a19ad57887c992aa6342ea2cf14ba28
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22543052"
---
# <a name="manage-office-365-groups-with-powershell"></a><span data-ttu-id="9dd0d-103">Administrar grupos de Office 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="9dd0d-103">Manage Office 365 Groups with PowerShell</span></span>

 <span data-ttu-id="9dd0d-104">*Última 18 de abril actualizados de 2018*</span><span class="sxs-lookup"><span data-stu-id="9dd0d-104">*Last updated 18 April, 2018*</span></span> 
  
<span data-ttu-id="9dd0d-p101">Este artículo proporciona los pasos para realizar tareas comunes de administración de grupos en PowerShell de Microsoft. También se enumeran los cmdlets de PowerShell para grupos. Para información sobre la administración de sitios de SharePoint, vea [administrar los sitios de grupo y los sitios de comunicación mediante el uso de PowerShell](https://support.office.com/article/52ecc2ab-88c3-486e-b8ff-ef6a968ccd87).</span><span class="sxs-lookup"><span data-stu-id="9dd0d-p101">This article provides the steps for doing common management tasks for Groups in Microsoft PowerShell. It also lists the PowerShell cmdlets for Groups. For info about managing SharePoint sites, see [Manage team sites and communication sites by using PowerShell](https://support.office.com/article/52ecc2ab-88c3-486e-b8ff-ef6a968ccd87).</span></span>
  
## <a name="common-tasks-for-managing-office-365-groups"></a><span data-ttu-id="9dd0d-108">Tareas comunes para administrar grupos de Office 365</span><span class="sxs-lookup"><span data-stu-id="9dd0d-108">Common tasks for managing Office 365 Groups</span></span>

- [<span data-ttu-id="9dd0d-109">Listas de distribución de actualización a Office 365 grupos en Outlook</span><span class="sxs-lookup"><span data-stu-id="9dd0d-109">Upgrade distribution lists to Office 365 Groups in Outlook</span></span>](https://support.office.com/article/787d7a75-e201-46f3-a242-f698162ff09f)
    
- [<span data-ttu-id="9dd0d-110">Administrar quién puede crear grupos de Office 365</span><span class="sxs-lookup"><span data-stu-id="9dd0d-110">Manage who can create Office 365 Groups</span></span>](https://support.office.com/article/4c46c8cb-17d0-44b5-9776-005fced8e618)
    
- [<span data-ttu-id="9dd0d-111">Administrar el acceso de invitado a los grupos de Office 365</span><span class="sxs-lookup"><span data-stu-id="9dd0d-111">Manage guest access to Office 365 Groups</span></span>](https://support.office.com/article/7c713d74-a144-4eab-92e7-d50df526ff96)
    
- [<span data-ttu-id="9dd0d-112">Administración de grupos de forma dinámica en Active Directory de Azure</span><span class="sxs-lookup"><span data-stu-id="9dd0d-112">Manage groups dynamically in Azure Active Directory</span></span>](https://go.microsoft.com/fwlink/?linkid=847632)
    
- <span data-ttu-id="9dd0d-113">Agregar cientos o miles de usuarios a los grupos de Office 365, use el [cmdlet Add-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616191).</span><span class="sxs-lookup"><span data-stu-id="9dd0d-113">Add hundreds or thousands of users to Office 365 groups, use the [Add-UnifiedGroupLinks cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=616191).</span></span>
    
### <a name="link-to-your-office-365-groups-usage-guidelines"></a><span data-ttu-id="9dd0d-114">Vínculo a las directrices de uso de grupos de Office 365</span><span class="sxs-lookup"><span data-stu-id="9dd0d-114">Link to your Office 365 Groups usage guidelines</span></span>
<span data-ttu-id="9dd0d-115"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="9dd0d-115"></span></span>

<span data-ttu-id="9dd0d-p102">Cuando los usuarios [crear un grupo en Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102), puede mostrarlos un vínculo a instrucciones sobre el uso de su organización. Por ejemplo, si se requiere un prefijo específico o sufijo que se agrega a un nombre de grupo.</span><span class="sxs-lookup"><span data-stu-id="9dd0d-p102">When users [Create a group in Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102), you can show them a link to your organization's usage guidelines. For example, if you require a specific prefix or suffix to be added to a group name.</span></span>
  
<span data-ttu-id="9dd0d-p103">Use Azure Active Directory PowerShell para dirigir a los usuarios a instrucciones de uso de la organización para los grupos de Office 365. Desproteger [los cmdlets de Azure Active Directory para configurar las opciones de grupo](https://go.microsoft.com/fwlink/?LinkID=827484) y siga los pasos de la **configuración de crear en el nivel de directorio** para definir el hipervínculo de pauta de uso. Una vez que se ejecuta el cmdlet AAD, usuario verán el vínculo a sus instrucciones que indican cuándo crean o edición un grupo en Outlook.</span><span class="sxs-lookup"><span data-stu-id="9dd0d-p103">Use the Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups. Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the usage guideline hyperlink. Once you run the AAD cmdlet, user's will see the link to your guidelines when they create or edit a group in Outlook.</span></span> 
  
![Crear un grupo nuevo con el vínculo de instrucciones de uso](./../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![Haga clic en directrices de uso de grupo para ver las organizaciones instrucciones de grupos de Office 365](./../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
### <a name="allow-users-to-send-as-the-office-365-group"></a><span data-ttu-id="9dd0d-123">Permitir a los usuarios enviar como el grupo de Office 365</span><span class="sxs-lookup"><span data-stu-id="9dd0d-123">Allow users to Send as the Office 365 Group</span></span>
<span data-ttu-id="9dd0d-124"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="9dd0d-124"></span></span>

<span data-ttu-id="9dd0d-p104">También puede hacerlo en el centro de administración de Exchange. Vea [miembros de permitir enviar como o enviar en nombre de un grupo](https://support.office.com/article/0ad41414-0cc6-4b97-90fb-06bec7bcf590).</span><span class="sxs-lookup"><span data-stu-id="9dd0d-p104">You can also do this in the Exchange Admin Center. See [Allow members to send as or send on behalf of a Group](https://support.office.com/article/0ad41414-0cc6-4b97-90fb-06bec7bcf590).</span></span>
  
<span data-ttu-id="9dd0d-p105">Si desea habilitar a los grupos de Office 365 para "Enviar como", use el [Complemento RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=723960) y los cmdlets [Get-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=733239) para realizar esta configuración. Una vez que se habilita a esta opción, los usuarios del grupo de Office 365 pueden usar Outlook o Outlook en la web para enviar y responder al correo electrónico como el grupo de Office 365. Los usuarios pueden ir al grupo, cree un correo electrónico nuevo y cambie el campo "Enviar como" a la dirección de correo electrónico del grupo.</span><span class="sxs-lookup"><span data-stu-id="9dd0d-p105">If you want to enable your Office 365 groups to "Send As", use the [Add-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=723960) and the [Get-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=733239) cmdlets to configure this. Once you enable this setting, Office 365 group users can use Outlook or Outlook on the web to send and reply to email as the Office 365 group. Users can go to the group, create a new email, and change the "Send As" field to the group's email address.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="9dd0d-130">Debe agregar la dirección de correo electrónico de grupo para el campo **Cc** al redactar el correo electrónico de "Enviar como", para que el mensaje se envía al grupo y aparece en las conversaciones en grupo.</span><span class="sxs-lookup"><span data-stu-id="9dd0d-130">You'll need to add the group email address to the **Cc** field when you compose the "send as" email, so that the message is sent to the Group and appears in group conversations.</span></span> 
  
<span data-ttu-id="9dd0d-131">En este momento, la única forma de actualizar la directiva de buzón de correo es a través de [PowerShell](https://technet.microsoft.com/en-us/library/cc482986.aspx).</span><span class="sxs-lookup"><span data-stu-id="9dd0d-131">At this time, the only way to update the mailbox policy is through [PowerShell](https://technet.microsoft.com/en-us/library/cc482986.aspx).</span></span>
  
- <span data-ttu-id="9dd0d-132">Use este comando para establecer el alias del grupo.</span><span class="sxs-lookup"><span data-stu-id="9dd0d-132">Use this command to set the group alias.</span></span>
    
  ```
  $groupAlias = "TestSendAs"
  ```

- <span data-ttu-id="9dd0d-133">Use este comando para establecer el alias del usuario.</span><span class="sxs-lookup"><span data-stu-id="9dd0d-133">Use this command to set the user alias.</span></span>
    
  ```
  $userAlias = "User"
  ```

- <span data-ttu-id="9dd0d-134">Use este comando para pasar la groupalias al cmdlet Get-Recipient para obtener los detalles de destinatario.</span><span class="sxs-lookup"><span data-stu-id="9dd0d-134">Use this command to pass the groupalias to the Get-Recipient cmdlet to get the recipient details.</span></span>
    
  ```
  $groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias
  ```

- <span data-ttu-id="9dd0d-p106">A continuación, se necesita el nombre del destinatario destino (nombre de grupo) que se pasan al cmdlet Add-RecipientPermission. El useralias para los que se concederá el permiso Enviar como se asignará al parámetro - Administrador de confianza.</span><span class="sxs-lookup"><span data-stu-id="9dd0d-p106">Then the target recipient name (Group name) needs to be passed to the Add-RecipientPermission cmdlet. The useralias for whom the sendas permission will be given will be assigned to the -Trustee parameter.</span></span>
    
  ```
  Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
  ```

- <span data-ttu-id="9dd0d-137">Una vez que se ejecuta el cmdlet, pueden ir a los usuarios a Outlook o Outlook en la web para enviar como el grupo, mediante la adición de la dirección de correo electrónico de grupo para el campo **de** .</span><span class="sxs-lookup"><span data-stu-id="9dd0d-137">Once the cmdlet is executed, users can go to Outlook or Outlook on the web to send as the group, by adding the group email address to the **From** field.</span></span> 
    
### <a name="create-classifications-for-office-groups-in-your-organization"></a><span data-ttu-id="9dd0d-138">Crear clasificaciones para los grupos de Office en su organización</span><span class="sxs-lookup"><span data-stu-id="9dd0d-138">Create classifications for Office groups in your organization</span></span>
<span data-ttu-id="9dd0d-139"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="9dd0d-139"></span></span>

<span data-ttu-id="9dd0d-p107">Puede crear clasificaciones de que los usuarios de su organización pueden establecer al crear un grupo de Office 365. Por ejemplo, puede permitir a los usuarios establecer "Estándar", "Secret" y "Top Secret" en grupos que se crean. Clasificaciones de grupo no se establecen de forma predeterminada y debe crear en orden para los usuarios a establecerla. Use Windows Azure Active Directory PowerShell para dirigir a los usuarios a instrucciones de uso de la organización para los grupos de Office 365.</span><span class="sxs-lookup"><span data-stu-id="9dd0d-p107">You can create classifications that the users in your organization can set when they create an Office 365 group. For example, you can allow users to set "Standard", "Secret", and "Top Secret" on groups they create. Group classifications aren't set by default and you need to create it in order for your users to set it. Use Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups.</span></span>
  
<span data-ttu-id="9dd0d-144">Desproteger [los cmdlets de Azure Active Directory para configurar las opciones de grupo](https://go.microsoft.com/fwlink/?LinkID=827484) y siga los pasos de la **configuración de crear en el nivel de directorio** para definir la clasificación de los grupos de Office 365.</span><span class="sxs-lookup"><span data-stu-id="9dd0d-144">Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the classification for Office 365 groups.</span></span> 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

<span data-ttu-id="9dd0d-145">Para asociar una descripción para cada clasificación que puede usar la configuración de atributo *ClassificationDescriptions* para definir.</span><span class="sxs-lookup"><span data-stu-id="9dd0d-145">In order to associate a description to each classification you can use the settings attribute  *ClassificationDescriptions*  to define.</span></span> 
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description", where Classification matches the strings in the ClassificationList.
```

<span data-ttu-id="9dd0d-146">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="9dd0d-146">For example:</span></span>
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

<span data-ttu-id="9dd0d-147">Después de ejecutar el cmdlet anterior de Azure Active Directory para establecer la clasificación de su, ejecute el cmdlet [Set-UnifiedGroup](https://go.microsoft.com/fwlink/?LinkID=616189) si desea establecer la clasificación de un grupo específico.</span><span class="sxs-lookup"><span data-stu-id="9dd0d-147">After you run the above Azure Active Directory cmdlet to set your classification, run the [Set-UnifiedGroup](https://go.microsoft.com/fwlink/?LinkID=616189) cmdlet if you want to set the classification for a specific group.</span></span> 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

<span data-ttu-id="9dd0d-148">O bien, crear un grupo nuevo con una clasificación.</span><span class="sxs-lookup"><span data-stu-id="9dd0d-148">Or create a new group with a classification.</span></span>
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

<span data-ttu-id="9dd0d-149">Desproteger [Using PowerShell con Exchange Online](https://go.microsoft.com/fwlink/?LinkID=402831) y [Connect to Exchange Online PowerShell](https://go.microsoft.com/fwlink/?LinkID=722415) para obtener más detalles sobre el uso de Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9dd0d-149">Check out [Using PowerShell with Exchange Online](https://go.microsoft.com/fwlink/?LinkID=402831) and [Connect to Exchange Online PowerShell](https://go.microsoft.com/fwlink/?LinkID=722415) for more details on using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="9dd0d-150">Una vez que estos valores están habilitados, el propietario del grupo podrán elegir una clasificación de la lista desplegable menú en Outlook en la Web y de Outlook y vuelva a guardarla desde la página de grupo **Editar** .</span><span class="sxs-lookup"><span data-stu-id="9dd0d-150">Once these settings are enabled, the group owner will be able to choose a classification from the drop down menu in Outlook on the Web and Outlook, and save it from the **Edit** group page.</span></span> 
  
![Elija la clasificación de grupo de Office 365](./../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
### <a name="hide-office-365-groups-from-gal"></a><span data-ttu-id="9dd0d-152">Ocultar los grupos de Office 365 desde la lista global de direcciones</span><span class="sxs-lookup"><span data-stu-id="9dd0d-152">Hide Office 365 Groups from GAL</span></span>
<span data-ttu-id="9dd0d-153"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="9dd0d-153"></span></span>

<span data-ttu-id="9dd0d-p108">Puede especificar si un grupo de Office 365 aparece en la lista global de direcciones (GAL) y otras listas de la organización. Por ejemplo, si tiene un grupo del departamento legal que no desea que aparezca en la lista de direcciones, puede detener ese grupo que no aparezca en la lista global de direcciones. Ejecutar el commandlet Set-Unified grupo para ocultar el grupo de la lista de direcciones como esta:</span><span class="sxs-lookup"><span data-stu-id="9dd0d-p108">You can specify whether a Office 365 group appears in the global address list (GAL) and other lists in your organization. For example, if you have a legal department group that you don't want to show up in the address list, you can stop that group from appearing in GAL. Run the Set-Unified Group commandlet to hide the group from address list like this:</span></span>
  
```
  Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

### <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a><span data-ttu-id="9dd0d-157">Permitir que sólo los usuarios internos enviar el mensaje al grupo de Office 365</span><span class="sxs-lookup"><span data-stu-id="9dd0d-157">Allow only internal users to send message to Office 365 group</span></span>
<span data-ttu-id="9dd0d-158"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="9dd0d-158"></span></span>

<span data-ttu-id="9dd0d-p109">Si no desea que los usuarios de otra organización para enviar correo electrónico a un grupo de Office 365, puede cambiar la configuración de ese grupo. Le permitirá que sólo los usuarios internos enviar un correo electrónico a su grupo. Si un usuario externo intenta enviar mensaje a ese grupo serán rechazadas.</span><span class="sxs-lookup"><span data-stu-id="9dd0d-p109">If you don't want users from other organization to send email to a Office 365 group, you can change the settings for that group. It will allow only internal users to send an email to your group. If external user try to send message to that group they will be rejected.</span></span>
  
<span data-ttu-id="9dd0d-162">Ejecutar el commandlet Set-UnifiedGroup para actualizar esta configuración, como la siguiente:</span><span class="sxs-lookup"><span data-stu-id="9dd0d-162">Run the Set-UnifiedGroup commandlet to update this setting, like this:</span></span>
  
```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

### <a name="add-mailtips-to-the-office-365-groups"></a><span data-ttu-id="9dd0d-163">Agregar sugerencias de correo electrónico a los grupos de Office 365</span><span class="sxs-lookup"><span data-stu-id="9dd0d-163">Add MailTips to the Office 365 Groups</span></span>
<span data-ttu-id="9dd0d-164"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="9dd0d-164"></span></span>

<span data-ttu-id="9dd0d-165">Cada vez que un remitente intenta enviar un correo electrónico a un grupo de Office 365, se puede mostrar una sugerencia de correo electrónico a él.</span><span class="sxs-lookup"><span data-stu-id="9dd0d-165">Whenever a sender tries to send an email to an Office 365 group, a MailTip can be shown to him.</span></span>
  
<span data-ttu-id="9dd0d-166">Ejecutar el commandlet Set-Unified grupo para agregar una sugerencia de correo electrónico para el grupo:</span><span class="sxs-lookup"><span data-stu-id="9dd0d-166">Run the Set-Unified Group commandlet to add a mailTip to the group:</span></span>
  
```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

<span data-ttu-id="9dd0d-p110">Junto con la sugerencia de correo electrónico, también puede establecer MailTipTranslations, que especifica los idiomas adicionales para la sugerencia de correo electrónico. Suponga que desea tener la traducción al español, a continuación, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="9dd0d-p110">Along with MailTip, you can also set MailTipTranslations, which specifies additional languages fro the MailTip. Suppose you want to have the Spanish translation, then run the following command:</span></span>
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

### <a name="change-display-name-of-the-office-365-group"></a><span data-ttu-id="9dd0d-169">Cambiar el nombre para mostrar del grupo de Office 365</span><span class="sxs-lookup"><span data-stu-id="9dd0d-169">Change Display name of the Office 365 group</span></span>
<span data-ttu-id="9dd0d-170"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="9dd0d-170"></span></span>

<span data-ttu-id="9dd0d-p111">Nombre para mostrar especifica el nombre del grupo de Office 365. Puede ver este nombre en el portal de administración de exchange admin center o o365. Puede editar el nombre para mostrar del grupo o asignar un nombre para mostrar para un grupo de Office 365 existentes mediante la ejecución de comando Set-UnifiedGroup:</span><span class="sxs-lookup"><span data-stu-id="9dd0d-p111">Display name specifies the name of the Office 365 group. You can see this name in your exchange admin center or o365 admin portal. You can edit the display name of the group or assign a display name to an exisiting Office 365 group by running Set-UnifiedGroup command:</span></span>
  
```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

### <a name="manage-user-photos-in-office-365-groups"></a><span data-ttu-id="9dd0d-174">Administrar fotos de usuario en grupos de Office 365</span><span class="sxs-lookup"><span data-stu-id="9dd0d-174">Manage user photos in Office 365 Groups</span></span>
<span data-ttu-id="9dd0d-175"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="9dd0d-175"></span></span>

<span data-ttu-id="9dd0d-176">| |</span><span class="sxs-lookup"><span data-stu-id="9dd0d-176"></span></span>
|<span data-ttu-id="9dd0d-177">**Nombre de cmdlet**</span><span class="sxs-lookup"><span data-stu-id="9dd0d-177">**Cmdlet name**</span></span>|<span data-ttu-id="9dd0d-178">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="9dd0d-178">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="9dd0d-179">Get-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="9dd0d-179">Get-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |<span data-ttu-id="9dd0d-p112">Se usa para ver información acerca de la foto de usuario asociada con una cuenta. Fotografías de usuario se almacenan en Active Directory</span><span class="sxs-lookup"><span data-stu-id="9dd0d-p112">Used to view information about the user photo associated with an account. User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="9dd0d-182">Set-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="9dd0d-182">Set-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |<span data-ttu-id="9dd0d-p113">Se usa para asociar una foto de usuario con una cuenta. Fotografías de usuario se almacenan en Active Directory</span><span class="sxs-lookup"><span data-stu-id="9dd0d-p113">Used to associate a user photo with an account. User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="9dd0d-185">Remove-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="9dd0d-185">Remove-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |<span data-ttu-id="9dd0d-186">Quitar la foto para un grupo de Office 365</span><span class="sxs-lookup"><span data-stu-id="9dd0d-186">Remove the photo for an Office 365 group</span></span>  <br/> |
   
### <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a><span data-ttu-id="9dd0d-187">Cambie la configuración predeterminada de Office 365 grupos para Outlook al público o privado</span><span class="sxs-lookup"><span data-stu-id="9dd0d-187">Change the default setting of Office 365 Groups for Outlook to Public or Private</span></span>
<span data-ttu-id="9dd0d-188"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="9dd0d-188"></span></span>

<span data-ttu-id="9dd0d-p114">Office 365 se crean grupos en Outlook como privadas de forma predeterminada. Si su organización desea que Office 365 grupos para Outlook que se creará como Public de forma predeterminada (o a la privada), use esta sintaxis de cmdlet de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="9dd0d-p114">Office 365 Groups in Outlook are created as Private by default. If your organization wants Office 365 Groups for Outlook to be created as Public by default (or back to Private), use this PowerShell cmdlet syntax:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
<span data-ttu-id="9dd0d-191">Para establecer Private:</span><span class="sxs-lookup"><span data-stu-id="9dd0d-191">To set to Private:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
<span data-ttu-id="9dd0d-192">Para comprobar la configuración:</span><span class="sxs-lookup"><span data-stu-id="9dd0d-192">To verify the setting:</span></span> 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
<span data-ttu-id="9dd0d-193">Para obtener más información, vea [Set-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871816) y [Get-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871817).</span><span class="sxs-lookup"><span data-stu-id="9dd0d-193">To learn more, see [Set-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871816) and [Get-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871817).</span></span>
  
## <a name="office-365-groups-cmdlets"></a><span data-ttu-id="9dd0d-194">Cmdlets de grupos de Office 365</span><span class="sxs-lookup"><span data-stu-id="9dd0d-194">Office 365 Groups cmdlets</span></span>

<span data-ttu-id="9dd0d-p115">Los cmdlets siguientes se han realizado recientemente disponibles para grupos de Office 365. Si no puede utilizar estos, su suscripción de Office 365 no se actualizó con esta funcionalidad aún. Compruebe la recepción de mensajes y la [Guía básica de Office 365](http://roadmap.office.com/en-us).</span><span class="sxs-lookup"><span data-stu-id="9dd0d-p115">The following cmdlets were recently made available to Office 365 Groups. If you aren't able to use these, your Office 365 subscription has not been updated with this functionality yet. Check your Message Center and the [Office 365 Roadmap](http://roadmap.office.com/en-us).</span></span>
  
<span data-ttu-id="9dd0d-198">| |</span><span class="sxs-lookup"><span data-stu-id="9dd0d-198"></span></span>
|<span data-ttu-id="9dd0d-199">**Nombre de cmdlet**</span><span class="sxs-lookup"><span data-stu-id="9dd0d-199">**Cmdlet name**</span></span>|<span data-ttu-id="9dd0d-200">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="9dd0d-200">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="9dd0d-201">Get-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="9dd0d-201">Get-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |<span data-ttu-id="9dd0d-202">Use este cmdlet para buscar los grupos existentes de Office 365 y para ver las propiedades del objeto de grupo</span><span class="sxs-lookup"><span data-stu-id="9dd0d-202">Use this cmdlet to look up existing Office 365 Groups, and to view properties of the group object</span></span>  <br/> |
|[<span data-ttu-id="9dd0d-203">Set-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="9dd0d-203">Set-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |<span data-ttu-id="9dd0d-204">Actualizar las propiedades de un determinado grupo de Office 365</span><span class="sxs-lookup"><span data-stu-id="9dd0d-204">Update the properties of a specific Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="9dd0d-205">New-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="9dd0d-205">New-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |<span data-ttu-id="9dd0d-p116">Crear un nuevo grupo de Office 365. Este cmdlet proporciona un conjunto mínimo de parámetros, para la configuración de los valores de las propiedades extendidas usar Set-UnifiedGroup después de crear el nuevo grupo</span><span class="sxs-lookup"><span data-stu-id="9dd0d-p116">Create a new Office 365 group. This cmdlet provides a minimal set of parameters, for setting values for extended properties use Set-UnifiedGroup after creating the new group</span></span>  <br/> |
|[<span data-ttu-id="9dd0d-208">Remove-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="9dd0d-208">Remove-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |<span data-ttu-id="9dd0d-209">Eliminar un grupo de 365 existente de Office</span><span class="sxs-lookup"><span data-stu-id="9dd0d-209">Delete an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="9dd0d-210">Get-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="9dd0d-210">Get-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |<span data-ttu-id="9dd0d-211">Recuperar información de pertenencia y el propietario de un grupo de Office 365</span><span class="sxs-lookup"><span data-stu-id="9dd0d-211">Retrieve membership and owner information for an Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="9dd0d-212">Add-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="9dd0d-212">Add-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |<span data-ttu-id="9dd0d-213">Agregar cientos o miles de usuarios o los propietarios de nuevo, a un grupo de 365 existente de Office</span><span class="sxs-lookup"><span data-stu-id="9dd0d-213">Add hundred or thousands of users, or new owners, to an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="9dd0d-214">Remove-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="9dd0d-214">Remove-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |<span data-ttu-id="9dd0d-215">Quitar los propietarios y los miembros de un grupo de 365 existente de Office</span><span class="sxs-lookup"><span data-stu-id="9dd0d-215">Remove owners and members from an existing Office 365 Group</span></span>  <br/> |
   
## <a name="for-more-information"></a><span data-ttu-id="9dd0d-216">Más información</span><span class="sxs-lookup"><span data-stu-id="9dd0d-216">For more information</span></span>

- [<span data-ttu-id="9dd0d-217">Uso de PowerShell</span><span class="sxs-lookup"><span data-stu-id="9dd0d-217">Using PowerShell</span></span>](https://technet.microsoft.com/en-us/library/cc482986.aspx)
    
- [<span data-ttu-id="9dd0d-218">Aplicar o quitar una directiva de buzón de Outlook Web App en un buzón</span><span class="sxs-lookup"><span data-stu-id="9dd0d-218">Apply or remove an Outlook Web App mailbox policy on a mailbox</span></span>](https://technet.microsoft.com/en-us/library/dd876884%28v=exchg.150%29.aspx)
    
- [<span data-ttu-id="9dd0d-219">Directiva de nomenclatura de grupos de Office 365</span><span class="sxs-lookup"><span data-stu-id="9dd0d-219">Office 365 Groups naming policy</span></span>](https://support.office.com/article/6ceca4d3-cad1-4532-9f0f-d469dfbbb552)
    

