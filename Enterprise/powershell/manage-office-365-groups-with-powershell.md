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
# <a name="manage-office-365-groups-with-powershell"></a>Administrar grupos de Office 365 con PowerShell

 *Última 18 de abril actualizados de 2018* 
  
Este artículo proporciona los pasos para realizar tareas comunes de administración de grupos en PowerShell de Microsoft. También se enumeran los cmdlets de PowerShell para grupos. Para información sobre la administración de sitios de SharePoint, vea [sitios de administración de SharePoint Online mediante PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).

## <a name="link-to-your-office-365-groups-usage-guidelines"></a>Vínculo a las directrices de uso de grupos de Office 365
<a name="BK_LinkToGuideLines"> </a>

Cuando los usuarios [crear o editar un grupo en Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), puede mostrarlos un vínculo a instrucciones sobre el uso de su organización. Por ejemplo, si se requiere un prefijo específico o sufijo que se agrega a un nombre de grupo.
  
Use Azure Active Directory PowerShell para dirigir a los usuarios a instrucciones de uso de la organización para los grupos de Office 365. Desproteger [los cmdlets de Azure Active Directory para configurar las opciones de grupo](https://go.microsoft.com/fwlink/?LinkID=827484) y siga los pasos de la **configuración de crear en el nivel de directorio** para definir el hipervínculo de pauta de uso. Una vez que se ejecuta el cmdlet AAD, usuario verán el vínculo a sus instrucciones que indican cuándo crean o edición un grupo en Outlook. 
  
![Crear un grupo nuevo con el vínculo de instrucciones de uso](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![Haga clic en directrices de uso de grupo para ver las organizaciones instrucciones de grupos de Office 365](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
## <a name="allow-users-to-send-as-the-office-365-group"></a>Permitir a los usuarios enviar como el grupo de Office 365
<a name="BK_LinkToGuideLines"> </a>
  
Si desea habilitar a los grupos de Office 365 para "Enviar como", use el [Complemento RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission) y los cmdlets [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient) para realizar esta configuración. Una vez que se habilita a esta opción, los usuarios del grupo de Office 365 pueden usar Outlook o Outlook en la web para enviar y responder al correo electrónico como el grupo de Office 365. Los usuarios pueden ir al grupo, cree un correo electrónico nuevo y cambie el campo "Enviar como" a la dirección de correo electrónico del grupo. 

([También puede hacerlo en el centro de administración de Exchange](https://docs.microsoft.com/en-us/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group)).
  
Use la siguiente secuencia de comandos, reemplazando * \<GroupAlias\> * con el alias del grupo que desea actualizar, y * \<UserAlias\> * con el alias del usuario a quien desea conceder permisos. [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) para ejecutar esta secuencia de comandos.

```PowerShell
$groupAlias = "<GroupAlias>"

$userAlias = "<UserAlias>"


$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

Una vez que se ejecuta el cmdlet, pueden ir a los usuarios a Outlook o Outlook en la web para enviar como el grupo, mediante la adición de la dirección de correo electrónico de grupo para el campo **de** . 

## <a name="create-classifications-for-office-groups-in-your-organization"></a>Crear clasificaciones para los grupos de Office en su organización

Puede crear clasificaciones de que los usuarios de su organización pueden establecer al crear un grupo de Office 365. Por ejemplo, puede permitir a los usuarios establecer "Estándar", "Secret" y "Top Secret" en grupos que se crean. Clasificaciones de grupo no se establecen de forma predeterminada y debe crear en orden para los usuarios a establecerla. Use Windows Azure Active Directory PowerShell para dirigir a los usuarios a instrucciones de uso de la organización para los grupos de Office 365.
  
Desproteger [los cmdlets de Azure Active Directory para configurar las opciones de grupo](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) y siga los pasos de la **configuración de crear en el nivel de directorio** para definir la clasificación de los grupos de Office 365. 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

Para asociar una descripción para cada clasificación que puede usar la configuración de atributo *ClassificationDescriptions* para definir.
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

donde clasificación coincide con las cadenas en el ClassificationList.

Ejemplo:
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

Después de ejecutar el cmdlet anterior de Azure Active Directory para establecer la clasificación de su, ejecute el cmdlet [Set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) si desea establecer la clasificación de un grupo específico. 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

O bien, crear un grupo nuevo con una clasificación.
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

Desproteger [Using PowerShell con Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) y [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) para obtener más detalles sobre el uso de Exchange Online PowerShell. 
  
Una vez que estos valores están habilitados, el propietario del grupo podrán elegir una clasificación de la lista desplegable menú en Outlook en la Web y de Outlook y vuelva a guardarla desde la página de grupo **Editar** . 
  
![Elija la clasificación de grupo de Office 365](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
## <a name="hide-office-365-groups-from-gal"></a>Ocultar los grupos de Office 365 desde la lista global de direcciones
<a name="BKMK_CreateClassification"> </a>

Puede especificar si un grupo de Office 365 aparece en la lista global de direcciones (GAL) y otras listas de la organización. Por ejemplo, si tiene un grupo del departamento legal que no desea que aparezca en la lista de direcciones, puede detener ese grupo que no aparezca en la lista global de direcciones. Ejecute el cmdlet de grupo de Set-Unified para ocultar el grupo de la lista de direcciones como esta:
  
```
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a>Permitir que sólo los usuarios internos enviar el mensaje al grupo de Office 365
<a name="BKMK_CreateClassification"> </a>

Si no desea que los usuarios de otra organización para enviar correo electrónico a un grupo de Office 365, puede cambiar la configuración de ese grupo. Le permitirá que sólo los usuarios internos enviar un correo electrónico a su grupo. Si un usuario externo intenta enviar mensaje a ese grupo serán rechazadas.
  
Ejecute el cmdlet Set-UnifiedGroup para actualizar esta configuración, como la siguiente:

```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-the-office-365-groups"></a>Agregar sugerencias de correo electrónico a los grupos de Office 365
<a name="BKMK_CreateClassification"> </a>

Cada vez que un remitente intenta enviar un correo electrónico a un grupo de Office 365, se puede mostrar una sugerencia de correo electrónico a ellos.
  
Ejecute el cmdlet de grupo de Set-Unified para agregar una sugerencia de correo electrónico para el grupo:

```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

Junto con la sugerencia de correo electrónico, también puede establecer MailTipTranslations, que especifica los idiomas adicionales para la sugerencia de correo electrónico. Suponga que desea tener la traducción al español, a continuación, ejecute el siguiente comando:
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-display-name-of-the-office-365-group"></a>Cambiar el nombre para mostrar del grupo de Office 365

Nombre para mostrar especifica el nombre del grupo de Office 365. Puede ver este nombre en el centro de administración de exchange o el portal de administración de Office 365. Puede editar el nombre para mostrar del grupo o asignar un nombre para mostrar a un grupo existente de Office 365, ejecute el comando Set-UnifiedGroup:

```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a>Cambie la configuración predeterminada de Office 365 grupos para Outlook al público o privado
<a name="BKMK_CreateClassification"> </a>

Office 365 se crean grupos en Outlook como privadas de forma predeterminada. Si su organización desea que Office 365 grupos que se creará como Public de forma predeterminada (o a la privada), use esta sintaxis de cmdlet de PowerShell:
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
Para establecer Private:
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
Para comprobar la configuración: 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
Para obtener más información, vea [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig) y [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig).
  
## <a name="office-365-groups-cmdlets"></a>Cmdlets de grupos de Office 365

Los cmdlets siguientes pueden usarse con Office 365 grupos.
  
|**Nombre de cmdlet**|**Descripción**|
|:-----|:-----|
|[Get-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |Use este cmdlet para buscar los grupos existentes de Office 365 y para ver las propiedades del objeto de grupo  <br/> |
|[Set-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |Actualizar las propiedades de un determinado grupo de Office 365  <br/> |
|[New-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |Crear un nuevo grupo de Office 365. Este cmdlet proporciona un conjunto mínimo de parámetros, para la configuración de los valores de las propiedades extendidas usar Set-UnifiedGroup después de crear el nuevo grupo  <br/> |
|[Remove-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |Eliminar un grupo de 365 existente de Office  <br/> |
|[Get-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |Recuperar información de pertenencia y el propietario de un grupo de Office 365  <br/> |
|[Add-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |Agregar cientos o miles de usuarios o los propietarios de nuevo, a un grupo de 365 existente de Office  <br/> |
|[Remove-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |Quitar los propietarios y los miembros de un grupo de 365 existente de Office  <br/> |
|[Get-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |Se usa para ver información acerca de la foto de usuario asociada con una cuenta. Fotografías de usuario se almacenan en Active Directory  <br/> |
|[Set-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |Se usa para asociar una foto de usuario con una cuenta. Fotografías de usuario se almacenan en Active Directory  <br/> |
|[Remove-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |Quitar la foto para un grupo de Office 365  <br/> |

## <a name="related-topics"></a>Temas relacionados

[Listas de distribución de actualización a los grupos de Office 365](https://docs.microsoft.com/en-us/office365/admin/manage/upgrade-distribution-lists)

[Administrar quién puede crear grupos de Office 365](https://docs.microsoft.com/en-us/office365/admin/create-groups/manage-creation-of-groups)

[Administrar el acceso de invitados a Grupos de Office 365](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[Cambiar la pertenencia al grupo estático a dinámico en](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-change-type)
