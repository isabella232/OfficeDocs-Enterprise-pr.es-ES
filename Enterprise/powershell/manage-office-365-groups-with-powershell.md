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
# <a name="manage-office-365-groups-with-powershell"></a>Administrar grupos de Office 365 con PowerShell

 *Última 18 de abril actualizados de 2018* 
  
Este artículo proporciona los pasos para realizar tareas comunes de administración de grupos en PowerShell de Microsoft. También se enumeran los cmdlets de PowerShell para grupos. Para información sobre la administración de sitios de SharePoint, vea [administrar los sitios de grupo y los sitios de comunicación mediante el uso de PowerShell](https://support.office.com/article/52ecc2ab-88c3-486e-b8ff-ef6a968ccd87).
  
## <a name="common-tasks-for-managing-office-365-groups"></a>Tareas comunes para administrar grupos de Office 365

- [Listas de distribución de actualización a Office 365 grupos en Outlook](https://support.office.com/article/787d7a75-e201-46f3-a242-f698162ff09f)
    
- [Administrar quién puede crear grupos de Office 365](https://support.office.com/article/4c46c8cb-17d0-44b5-9776-005fced8e618)
    
- [Administrar el acceso de invitado a los grupos de Office 365](https://support.office.com/article/7c713d74-a144-4eab-92e7-d50df526ff96)
    
- [Administración de grupos de forma dinámica en Active Directory de Azure](https://go.microsoft.com/fwlink/?linkid=847632)
    
- Agregar cientos o miles de usuarios a los grupos de Office 365, use el [cmdlet Add-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616191).
    
### <a name="link-to-your-office-365-groups-usage-guidelines"></a>Vínculo a las directrices de uso de grupos de Office 365
<a name="BK_LinkToGuideLines"> </a>

Cuando los usuarios [crear un grupo en Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102), puede mostrarlos un vínculo a instrucciones sobre el uso de su organización. Por ejemplo, si se requiere un prefijo específico o sufijo que se agrega a un nombre de grupo.
  
Use Azure Active Directory PowerShell para dirigir a los usuarios a instrucciones de uso de la organización para los grupos de Office 365. Desproteger [los cmdlets de Azure Active Directory para configurar las opciones de grupo](https://go.microsoft.com/fwlink/?LinkID=827484) y siga los pasos de la **configuración de crear en el nivel de directorio** para definir el hipervínculo de pauta de uso. Una vez que se ejecuta el cmdlet AAD, usuario verán el vínculo a sus instrucciones que indican cuándo crean o edición un grupo en Outlook. 
  
![Crear un grupo nuevo con el vínculo de instrucciones de uso](./../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![Haga clic en directrices de uso de grupo para ver las organizaciones instrucciones de grupos de Office 365](./../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
### <a name="allow-users-to-send-as-the-office-365-group"></a>Permitir a los usuarios enviar como el grupo de Office 365
<a name="BK_LinkToGuideLines"> </a>

También puede hacerlo en el centro de administración de Exchange. Vea [miembros de permitir enviar como o enviar en nombre de un grupo](https://support.office.com/article/0ad41414-0cc6-4b97-90fb-06bec7bcf590).
  
Si desea habilitar a los grupos de Office 365 para "Enviar como", use el [Complemento RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=723960) y los cmdlets [Get-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=733239) para realizar esta configuración. Una vez que se habilita a esta opción, los usuarios del grupo de Office 365 pueden usar Outlook o Outlook en la web para enviar y responder al correo electrónico como el grupo de Office 365. Los usuarios pueden ir al grupo, cree un correo electrónico nuevo y cambie el campo "Enviar como" a la dirección de correo electrónico del grupo. 
  
> [!NOTE]
> Debe agregar la dirección de correo electrónico de grupo para el campo **Cc** al redactar el correo electrónico de "Enviar como", para que el mensaje se envía al grupo y aparece en las conversaciones en grupo. 
  
En este momento, la única forma de actualizar la directiva de buzón de correo es a través de [PowerShell](https://technet.microsoft.com/en-us/library/cc482986.aspx).
  
- Use este comando para establecer el alias del grupo.
    
  ```
  $groupAlias = "TestSendAs"
  ```

- Use este comando para establecer el alias del usuario.
    
  ```
  $userAlias = "User"
  ```

- Use este comando para pasar la groupalias al cmdlet Get-Recipient para obtener los detalles de destinatario.
    
  ```
  $groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias
  ```

- A continuación, se necesita el nombre del destinatario destino (nombre de grupo) que se pasan al cmdlet Add-RecipientPermission. El useralias para los que se concederá el permiso Enviar como se asignará al parámetro - Administrador de confianza.
    
  ```
  Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
  ```

- Una vez que se ejecuta el cmdlet, pueden ir a los usuarios a Outlook o Outlook en la web para enviar como el grupo, mediante la adición de la dirección de correo electrónico de grupo para el campo **de** . 
    
### <a name="create-classifications-for-office-groups-in-your-organization"></a>Crear clasificaciones para los grupos de Office en su organización
<a name="BKMK_CreateClassification"> </a>

Puede crear clasificaciones de que los usuarios de su organización pueden establecer al crear un grupo de Office 365. Por ejemplo, puede permitir a los usuarios establecer "Estándar", "Secret" y "Top Secret" en grupos que se crean. Clasificaciones de grupo no se establecen de forma predeterminada y debe crear en orden para los usuarios a establecerla. Use Windows Azure Active Directory PowerShell para dirigir a los usuarios a instrucciones de uso de la organización para los grupos de Office 365.
  
Desproteger [los cmdlets de Azure Active Directory para configurar las opciones de grupo](https://go.microsoft.com/fwlink/?LinkID=827484) y siga los pasos de la **configuración de crear en el nivel de directorio** para definir la clasificación de los grupos de Office 365. 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

Para asociar una descripción para cada clasificación que puede usar la configuración de atributo *ClassificationDescriptions* para definir. 
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description", where Classification matches the strings in the ClassificationList.
```

Por ejemplo:
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

Después de ejecutar el cmdlet anterior de Azure Active Directory para establecer la clasificación de su, ejecute el cmdlet [Set-UnifiedGroup](https://go.microsoft.com/fwlink/?LinkID=616189) si desea establecer la clasificación de un grupo específico. 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

O bien, crear un grupo nuevo con una clasificación.
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

Desproteger [Using PowerShell con Exchange Online](https://go.microsoft.com/fwlink/?LinkID=402831) y [Connect to Exchange Online PowerShell](https://go.microsoft.com/fwlink/?LinkID=722415) para obtener más detalles sobre el uso de Exchange Online PowerShell. 
  
Una vez que estos valores están habilitados, el propietario del grupo podrán elegir una clasificación de la lista desplegable menú en Outlook en la Web y de Outlook y vuelva a guardarla desde la página de grupo **Editar** . 
  
![Elija la clasificación de grupo de Office 365](./../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
### <a name="hide-office-365-groups-from-gal"></a>Ocultar los grupos de Office 365 desde la lista global de direcciones
<a name="BKMK_CreateClassification"> </a>

Puede especificar si un grupo de Office 365 aparece en la lista global de direcciones (GAL) y otras listas de la organización. Por ejemplo, si tiene un grupo del departamento legal que no desea que aparezca en la lista de direcciones, puede detener ese grupo que no aparezca en la lista global de direcciones. Ejecutar el commandlet Set-Unified grupo para ocultar el grupo de la lista de direcciones como esta:
  
```
  Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

### <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a>Permitir que sólo los usuarios internos enviar el mensaje al grupo de Office 365
<a name="BKMK_CreateClassification"> </a>

Si no desea que los usuarios de otra organización para enviar correo electrónico a un grupo de Office 365, puede cambiar la configuración de ese grupo. Le permitirá que sólo los usuarios internos enviar un correo electrónico a su grupo. Si un usuario externo intenta enviar mensaje a ese grupo serán rechazadas.
  
Ejecutar el commandlet Set-UnifiedGroup para actualizar esta configuración, como la siguiente:
  
```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

### <a name="add-mailtips-to-the-office-365-groups"></a>Agregar sugerencias de correo electrónico a los grupos de Office 365
<a name="BKMK_CreateClassification"> </a>

Cada vez que un remitente intenta enviar un correo electrónico a un grupo de Office 365, se puede mostrar una sugerencia de correo electrónico a él.
  
Ejecutar el commandlet Set-Unified grupo para agregar una sugerencia de correo electrónico para el grupo:
  
```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

Junto con la sugerencia de correo electrónico, también puede establecer MailTipTranslations, que especifica los idiomas adicionales para la sugerencia de correo electrónico. Suponga que desea tener la traducción al español, a continuación, ejecute el siguiente comando:
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

### <a name="change-display-name-of-the-office-365-group"></a>Cambiar el nombre para mostrar del grupo de Office 365
<a name="BKMK_CreateClassification"> </a>

Nombre para mostrar especifica el nombre del grupo de Office 365. Puede ver este nombre en el portal de administración de exchange admin center o o365. Puede editar el nombre para mostrar del grupo o asignar un nombre para mostrar para un grupo de Office 365 existentes mediante la ejecución de comando Set-UnifiedGroup:
  
```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

### <a name="manage-user-photos-in-office-365-groups"></a>Administrar fotos de usuario en grupos de Office 365
<a name="BKMK_CreateClassification"> </a>

| |
|**Nombre de cmdlet**|**Descripción**|
|:-----|:-----|
|[Get-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |Se usa para ver información acerca de la foto de usuario asociada con una cuenta. Fotografías de usuario se almacenan en Active Directory  <br/> |
|[Set-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |Se usa para asociar una foto de usuario con una cuenta. Fotografías de usuario se almacenan en Active Directory  <br/> |
|[Remove-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |Quitar la foto para un grupo de Office 365  <br/> |
   
### <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a>Cambie la configuración predeterminada de Office 365 grupos para Outlook al público o privado
<a name="BKMK_CreateClassification"> </a>

Office 365 se crean grupos en Outlook como privadas de forma predeterminada. Si su organización desea que Office 365 grupos para Outlook que se creará como Public de forma predeterminada (o a la privada), use esta sintaxis de cmdlet de PowerShell:
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
Para establecer Private:
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
Para comprobar la configuración: 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
Para obtener más información, vea [Set-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871816) y [Get-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871817).
  
## <a name="office-365-groups-cmdlets"></a>Cmdlets de grupos de Office 365

Los cmdlets siguientes se han realizado recientemente disponibles para grupos de Office 365. Si no puede utilizar estos, su suscripción de Office 365 no se actualizó con esta funcionalidad aún. Compruebe la recepción de mensajes y la [Guía básica de Office 365](http://roadmap.office.com/en-us).
  
| |
|**Nombre de cmdlet**|**Descripción**|
|:-----|:-----|
|[Get-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |Use este cmdlet para buscar los grupos existentes de Office 365 y para ver las propiedades del objeto de grupo  <br/> |
|[Set-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |Actualizar las propiedades de un determinado grupo de Office 365  <br/> |
|[New-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |Crear un nuevo grupo de Office 365. Este cmdlet proporciona un conjunto mínimo de parámetros, para la configuración de los valores de las propiedades extendidas usar Set-UnifiedGroup después de crear el nuevo grupo  <br/> |
|[Remove-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |Eliminar un grupo de 365 existente de Office  <br/> |
|[Get-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |Recuperar información de pertenencia y el propietario de un grupo de Office 365  <br/> |
|[Add-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |Agregar cientos o miles de usuarios o los propietarios de nuevo, a un grupo de 365 existente de Office  <br/> |
|[Remove-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |Quitar los propietarios y los miembros de un grupo de 365 existente de Office  <br/> |
   
## <a name="for-more-information"></a>Más información

- [Uso de PowerShell](https://technet.microsoft.com/en-us/library/cc482986.aspx)
    
- [Aplicar o quitar una directiva de buzón de Outlook Web App en un buzón](https://technet.microsoft.com/en-us/library/dd876884%28v=exchg.150%29.aspx)
    
- [Directiva de nomenclatura de grupos de Office 365](https://support.office.com/article/6ceca4d3-cad1-4532-9f0f-d469dfbbb552)
    

