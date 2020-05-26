---
title: Administrar grupos de Office 365 con PowerShell
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
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
ms.openlocfilehash: a9b481d7448c65a8860ef44d6d7f8980c3dd91d8
ms.sourcegitcommit: ee6fcb8c78de748fa203deacf799f66ad99f18e1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2020
ms.locfileid: "44352960"
---
# <a name="manage-office-365-groups-with-powershell"></a>Administrar grupos de Office 365 con PowerShell

 *Última actualización el 18 de abril de 2018* 
  
En este artículo se describen los pasos para realizar tareas de administración comunes para los grupos de Microsoft PowerShell. También muestra los cmdlets de PowerShell para grupos. Para obtener información sobre la administración de sitios de SharePoint, vea [administrar sitios de SharePoint Online con PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).

## <a name="link-to-your-office-365-groups-usage-guidelines"></a>Vínculo a las instrucciones de uso de los grupos de Office 365
<a name="BK_LinkToGuideLines"> </a>

Cuando los usuarios [creen o editen un grupo en Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), podrá mostrarles un vínculo a las instrucciones de uso de su organización. Por ejemplo, si necesita agregar un prefijo o un sufijo específico a un nombre de grupo.
  
Use Azure Active Directory PowerShell para apuntar a los usuarios a las directrices de uso de su organización para los grupos de Office 365. Consulte [Azure Active Directory cmdlets para configurar las opciones de grupo](https://go.microsoft.com/fwlink/?LinkID=827484) y siga los pasos que se indican en el vínculo **crear configuración a nivel de directorio** para definir el hipervínculo de la instrucción de uso. Una vez que se haya ejecutado el cmdlet de AAD, el usuario verá el vínculo a las directrices al crear o editar un grupo en Outlook. 
  
![Crear un nuevo grupo con el vínculo de instrucciones de uso](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![Haga clic en instrucciones de uso de grupos para ver las directrices de grupos de Office 365](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
## <a name="allow-users-to-send-as-the-office-365-group"></a>Permitir que los usuarios envíen como el grupo de Office 365
<a name="BK_LinkToGuideLines"> </a>
  
Si desea habilitar los grupos de Office 365 en "enviar como", use los cmdlets [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/Add-RecipientPermission) y [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/Get-Recipient) para configurarlos. Una vez habilitada esta opción, los usuarios de grupo de Office 365 pueden usar Outlook o Outlook en la web para enviar y responder correo electrónico como el grupo de Office 365. Los usuarios pueden ir al grupo, crear un nuevo correo electrónico y cambiar el campo "enviar como" por la dirección de correo electrónico del grupo. 

([También puede hacerlo en el centro de administración de Exchange](https://docs.microsoft.com/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group)).
  
Use el siguiente script, reemplazando * \< GroupAlias \> * por el alias del grupo que desea actualizar y * \< UserAlias \> * con el alias del usuario al que desea conceder permssions. [Conéctese a Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) para ejecutar este script.

```PowerShell
$groupAlias = "<GroupAlias>"

$userAlias = "<UserAlias>"


$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

Una vez que se ejecuta el cmdlet, los usuarios pueden ir a Outlook o Outlook en la web para enviarlos como grupo, agregando la dirección de correo electrónico del grupo al campo **de** . 

## <a name="create-classifications-for-office-groups-in-your-organization"></a>Crear clasificaciones para los grupos de Office en su organización

Puede crear clasificaciones que los usuarios de la organización pueden establecer al crear un grupo de Office 365. Por ejemplo, puede permitir que los usuarios establezcan "Standard", "Secret" y "Top Secret" en los grupos que crean. Las clasificaciones de grupo no se establecen de forma predeterminada y es necesario crearlas para que los usuarios las configuren. Use Azure Active Directory PowerShell para dirigir a los usuarios a las instrucciones de uso de la organización para los grupos de Office 365.
  
Consulte los [cmdlets de Azure Active Directory para configurar las opciones de grupo](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) y siga los pasos descritos en la **opción crear configuración a nivel de directorio** para definir la clasificación de los grupos de Office 365. 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

Para asociar una descripción a cada clasificación, puede usar el atributo Settings *ClassificationDescriptions* para definirla.
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

donde clasificación coincide con las cadenas de ClassificationList.

Ejemplo:
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

Después de ejecutar el cmdlet de Azure Active Directory anterior para establecer la clasificación, ejecute el cmdlet [set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/Set-UnifiedGroup) si desea establecer la clasificación para un grupo específico. 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

O bien, cree un nuevo grupo con una clasificación.
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

Vea [usar PowerShell con Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) y [Conéctese a Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) para obtener más información sobre el uso de Exchange Online PowerShell. 
  
Una vez habilitada esta configuración, el propietario del grupo podrá elegir una clasificación en el menú desplegable de Outlook en la web y en Outlook, y guardarla desde la página **Editar** grupo. 
  
![Elegir la clasificación de grupo de Office 365](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
## <a name="hide-office-365-groups-from-gal"></a>Ocultar grupos de Office 365 desde GAL
<a name="BKMK_CreateClassification"> </a>

Puede especificar si un grupo de Office 365 aparece en la lista global de direcciones (GAL) y en otras listas de la organización. Por ejemplo, si tiene un grupo de departamento legal que no desea que aparezca en la lista de direcciones, puede impedir que ese grupo aparezca en la GAL. Ejecute el cmdlet Set-Unified Group para ocultar el grupo de la lista de direcciones de la siguiente manera:
  
```
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a>Permitir que solo los usuarios internos envíen mensajes al grupo de Office 365
<a name="BKMK_CreateClassification"> </a>

Si no quiere que los usuarios de otras organizaciones envíen correo electrónico a un grupo de Office 365, puede cambiar la configuración de ese grupo. Permitirá que solo los usuarios internos envíen un correo electrónico a su grupo. Si un usuario externo intenta enviar un mensaje a ese grupo, se rechazará.
  
Ejecute el cmdlet Set-UnifiedGroup para actualizar esta configuración, como se muestra a continuación:

```
Set-UnifiedGroup -Identity "Internal senders only" -RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-the-office-365-groups"></a>Agregar sugerencias de correo a los grupos de Office 365
<a name="BKMK_CreateClassification"> </a>

Cuando un remitente intenta enviar un correo electrónico a un grupo de Office 365, se le puede mostrar una sugerencia de correo electrónico.
  
Ejecute el cmdlet Set-Unified Group para agregar una sugerencia de correo al Grupo:

```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

Además de la sugerencia de correo, también puede establecer MailTipTranslations, que especifica los idiomas adicionales para la sugerencia de correo. Suponga que quiere tener la traducción al español y, a continuación, ejecute el siguiente comando:
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-display-name-of-the-office-365-group"></a>Cambiar el nombre para mostrar del grupo de Office 365

Nombre para mostrar especifica el nombre del grupo de Office 365. Puede ver este nombre en su centro de administración de Exchange o en el portal de administración de Office 365. Puede editar el nombre para mostrar del grupo o asignar un nombre para mostrar a un grupo existente de Office 365 mediante la ejecución del comando set-UnifiedGroup:

```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a>Cambiar la configuración predeterminada de Office 365 Groups para Outlook a Public o Private
<a name="BKMK_CreateClassification"> </a>

Office 365 grupos en Outlook se crean como privados de forma predeterminada. Si su organización desea que los grupos de Office 365 se creen como públicos de forma predeterminada (o volver a privado), use esta sintaxis de cmdlet de PowerShell:
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
Para establecer en privado:
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
Para comprobar la configuración: 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
Para obtener más información, consulte [set-organizationconfig](https://docs.microsoft.com/powershell/module/exchange/set-organizationconfig) y [Get-organizationconfig](https://docs.microsoft.com/powershell/module/exchange/Get-OrganizationConfig).
  
## <a name="office-365-groups-cmdlets"></a>Cmdlets de grupos de Office 365

Los siguientes cmdlets se pueden usar con los grupos de Office 365.
  
|**Nombre de cmdlet**|**Descripción**|
|:-----|:-----|
|[Get-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |Use este cmdlet para buscar grupos existentes de Office 365 y para ver las propiedades del objeto de grupo.  <br/> |
|[Set-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |Actualizar las propiedades de un grupo específico de Office 365  <br/> |
|[New-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |Cree un nuevo grupo de Office 365. Este cmdlet proporciona un conjunto mínimo de parámetros para establecer los valores de las propiedades extendidas usando Set-UnifiedGroup después de crear el nuevo grupo.  <br/> |
|[Remove-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |Eliminar un grupo existente de Office 365  <br/> |
|[Get-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |Recuperar la información de pertenencia y propietario de un grupo de Office 365  <br/> |
|[Add-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |Agregar cientos o miles de usuarios, o propietarios nuevos, a un grupo existente de Office 365  <br/> |
|[Remove-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |Quitar propietarios y miembros de un grupo existente de Office 365  <br/> |
|[Get-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |Se usa para ver información sobre la foto de usuario asociada a una cuenta. Las fotos de los usuarios se almacenan en Active Directory  <br/> |
|[Set-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |Se usa para asociar una foto de usuario con una cuenta. Las fotos de los usuarios se almacenan en Active Directory  <br/> |
|[Remove-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |Quitar la foto de un grupo de Office 365  <br/> |

## <a name="related-topics"></a>Temas relacionados

[Actualizar listas de distribución a grupos de Office 365](https://docs.microsoft.com/office365/admin/manage/upgrade-distribution-lists)

[Administrar quién puede crear grupos de Office 365](https://docs.microsoft.com/office365/admin/create-groups/manage-creation-of-groups)

[Administrar el acceso de invitados a los grupos de Office 365](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[Cambiar la pertenencia al grupo estático a dinámico](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-change-type)
