---
title: Administrar un sitio de grupo SharePoint Online aislado
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_Solutions
ms.assetid: 79a61003-4905-4ba8-9e8a-16def7add37c
description: 'Resumen: Administrar el sitio SharePoint Online del grupo aislado con estos procedimientos.'
ms.openlocfilehash: 516bf9d1c94992789bd8341b347a5788dbb04933
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2017
---
# <a name="manage-an-isolated-sharepoint-online-team-site"></a>Administrar un sitio de grupo SharePoint Online aislado

 **Resumen:** Administrar el sitio SharePoint Online del grupo aislado con estos procedimientos.
  
Este artículo describe las operaciones comunes de administración de un sitio de grupo SharePoint Online aislado.
  
## <a name="add-a-new-user"></a>Agregar un nuevo usuario

Cuando alguien nuevo une al sitio, debe decidir su nivel de participación en el sitio:
  
- Administración: Agregue la nueva cuenta de usuario para el sitio de grupo de acceso de administradores
    
- Colaboración activa: agregar la cuenta de usuario para el sitio de grupo de acceso a miembros
    
- Ver: Agregar la cuenta de usuario en el sitio los participantes ver grupo
    
Si está administrando cuentas de usuario y grupos a través de servidor de Active Directory (AD) de Windows, agregue los usuarios adecuados a los grupos de acceso apropiado mediante sus normal Windows Server AD usuario y grupo de procedimientos de gestión y espere a que la sincronización con su Suscripción de Office 365.
  
Si está administrando cuentas de usuario y grupos mediante Office 365, puede utilizar el centro de administración de Office o Microsoft PowerShell:
  
- Para el centro de administración de Office, inicie sesión con una cuenta de usuario que se ha asignado la función de administrador de la cuenta de usuario o administrador de la empresa y usar grupos para agregar los usuarios adecuados a los grupos de acceso apropiado.
    
- Para PowerShell, primero [conecte con el módulo de Active Directory V2 PowerShell de Azure](https://go.microsoft.com/fwlink/?linkid=842218). Para agregar una cuenta de usuario a un grupo de acceso mediante su nombre principal de usuario (UPN), utilice el siguiente bloque de comandos de PowerShell:
    
```
$userUPN="<UPN of the user account>"
$grpName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

> [!TIP]
> Para un archivo de texto que contiene todos los comandos de PowerShell y un Excel hoja de trabajo de configuración que genera comandos de PowerShell basándose en su grupo y usuario nombres de cuenta, descargue el [Aislado SharePoint Online sitio Deployment Kit de equipo](https://gallery.technet.microsoft.com/Isolated-SharePoint-Online-0b364907). 

Para agregar una cuenta de usuario a un grupo de acceso con su nombre para mostrar, utilice el siguiente bloque de comandos de PowerShell:

```
$userDisplayName="<display name of the user account>"
$grpName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userDisplayName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

## <a name="add-a-new-group"></a>Agregar un nuevo grupo

Para obtener acceso a todo un grupo, debe decidir el nivel de la participación de todos los miembros del grupo en el sitio:
  
- Administración: Agregar el grupo al sitio de grupo de acceso de administradores
    
- Colaboración activa: agregar el grupo al sitio de grupo de acceso a miembros
    
- Ver: Agregar el grupo al sitio visores acceder a grupo
    
Si está administrando cuentas de usuario y grupos de AD del servidor de Windows, agregar los grupos correspondientes a los grupos apropiados con su usuario de AD del servidor Windows normal y procedimientos de administración de grupo y espere a que la sincronización con su suscripción de Office 365.
  
Si está administrando cuentas de usuario y grupos mediante Office 365, puede utilizar el centro de administración de Office o PowerShell:
  
- Para el centro de administración de Office, inicie sesión con una cuenta de usuario que se ha asignado la función de administrador de la cuenta de usuario o administrador de la empresa y usar grupos para agregar los grupos correspondientes a los grupos de acceso apropiado.
    
- Para PowerShell, primero [conecte con el módulo de Active Directory V2 PowerShell de Azure](https://go.microsoft.com/fwlink/?linkid=842218). A continuación, utilice los siguientes comandos de PowerShell:
 
```
$newGroupName="<display name of the new group to add>"
$siteGrpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $newGroupName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $siteGrpName }).ObjectID
```

## <a name="remove-a-user"></a>Quitar un usuario

Cuando el acceso de un usuario debe quitarse del sitio, se eliminen en el grupo de acceso de las que actualmente son un miembro basado en su participación en el sitio:
  
- Administración: Quitar la cuenta de usuario del grupo de acceso de administradores de sitio
    
- Colaboración activa: quitar la cuenta de usuario del grupo de acceso de los miembros de sitio
    
- Visualización: Quitar la cuenta de usuario del grupo de acceso de sitio visores
    
Si está administrando cuentas de usuario y grupos de AD del servidor de Windows, quitar los usuarios adecuados de los grupos de acceso apropiada con su usuario de AD del servidor Windows normal y procedimientos de administración de grupo y espere a que la sincronización con el Office 365 suscripción.
  
Si está administrando cuentas de usuario y grupos mediante Office 365, puede utilizar el centro de administración de Office o PowerShell:
  
- Para el centro de administración de Office, inicie sesión con una cuenta de usuario que se ha asignado la función de administrador de la cuenta de usuario o administrador de la empresa y utilizar grupos para quitar los usuarios adecuados de los grupos de acceso apropiado.
    
- Para PowerShell, primero [conecte con el módulo de Active Directory V2 PowerShell de Azure](https://go.microsoft.com/fwlink/?linkid=842218). Para quitar una cuenta de usuario de un grupo de acceso con su UPN, utilice el siguiente bloque de comandos de PowerShell:
    
```
$userUPN="<UPN of the user account>"
$grpName="<display name of the access group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

Para quitar una cuenta de usuario de un grupo de acceso con su nombre para mostrar, utilice el siguiente bloque de comandos de PowerShell:
    
```
$userDisplayName="<display name of the user account>"
$grpName="<display name of the access group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userDisplayName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

## <a name="remove-a-group"></a>Quitar un grupo

Para quitar el acceso de un grupo entero, quita el grupo desde el grupo de acceso de las que actualmente son un miembro basado en su participación en el sitio:
  
- Administración: Quitar el grupo desde el grupo de acceso de administradores de sitio
    
- Colaboración activa: quitar el grupo de grupo de acceso de miembros del sitio
    
- Visualización: Quitar el grupo desde el grupo de acceso de sitio visores
    
Si está administrando cuentas de usuario y grupos de Active Directory de Windows Server, quite los grupos correspondientes de los grupos de acceso apropiado mediante sus normal Windows Server AD usuario y grupo de procedimientos de administración y espere a que la sincronización con su Suscripción de Office 365.
  
Si está administrando cuentas de usuario y grupos mediante Office 365, puede utilizar el centro de administración de Office o PowerShell:
  
- Para el centro de administración de Office, inicie sesión con una cuenta de usuario que se ha asignado la función de administrador de la cuenta de usuario o administrador de la empresa y utilizar grupos para quitar los grupos correspondientes de los grupos de acceso apropiado.
    
- Para PowerShell, primero [conecte con el módulo de Active Directory V2 PowerShell de Azure](https://go.microsoft.com/fwlink/?linkid=842218).    
Para quitar un grupo de un grupo de acceso utilizando sus nombres para mostrar, utilice el siguiente bloque de comandos de PowerShell:
    
```
$groupMemberName="<display name of the group to remove>"
$grpName="<display name of the access group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

## <a name="create-a-documents-subfolder-with-custom-permissions"></a>Crear una subcarpeta en documentos con permisos personalizados

En algunos casos, un subconjunto de las personas que trabajan en el sitio aislado necesita un lugar más privado para colaborar. Para los sitios de SharePoint Online, puede crear una subcarpeta en la carpeta de documentos del sitio y asignar permisos personalizados. Los que no tienen permisos no podrán ver la subcarpeta.
  
Para crear una subcarpeta en documentos con permisos personalizados, siga este procedimiento:
  
1. Iniciar sesión en Office 365 con una cuenta que sea miembro del grupo Administradores de acceso para el sitio. Para obtener ayuda, visite [dónde puede iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Ir al sitio del grupo aislado y haga clic en **documentos**.
    
3. Vaya a la carpeta en la carpeta de documentos que contendrá la subcarpeta con permisos personalizados, cree la carpeta y, a continuación, ábralo.
    
4. Haga clic en **Compartir**.
    
5. Haga clic en **compartido con > avanzada**.
    
6. Haga clic en **Detener la herencia de permisos**y, a continuación, haga clic en **Aceptar**.
    
7. Haga clic en **Compartir**.
    
8. Haga clic en **compartido con > avanzada**.
    
9. Haga clic en **conceder permisos > compartido con > avanzada**.
    
10. En la página permisos, haga clic en ** \<nombre del sitio > integrantes de la lista**.
    
11. En la ** \<nombre del sitio > miembros** de página, seleccione la marca de verificación junto a grupo de acceso de miembros del sitio, haga clic en **acciones**, haga clic en **quitar usuarios del grupo**y, a continuación, haga clic en **Aceptar**.
    
12. Para agregar los miembros específicos para esta subcarpeta, haga clic en **Nuevo > Agregar usuarios**.
    
13. En el cuadro de diálogo **Compartir** , escriba los nombres de las cuentas de usuario que pueden colaborar en los archivos de la subcarpeta y, a continuación, haga clic en **Compartir**.
    
14. Actualizar la página web para ver los nuevos resultados.
    
15. En **los grupos** en la exploración de la izquierda, haga clic en el ** \<nombre del sitio > visitantes** grupo y siga los pasos del 11 al 14 para especificar el conjunto de cuentas de usuario que puede ver los archivos en la subcarpeta (según sea necesario).
    
16. En **los grupos** en la exploración de la izquierda, haga clic en el ** \<nombre del sitio > propietarios** grupo y siga los pasos del 11 al 14 para especificar el conjunto de cuentas de usuario que puede administrar los permisos en la subcarpeta (según sea necesario).
    
17. Cierre la ficha **personas y grupos** en el explorador.
    
## <a name="see-also"></a>See Also

[Sitios de equipo de SharePoint Online aislados](isolated-sharepoint-online-team-sites.md)
  
[Diseñar un sitio de grupo SharePoint Online aislado](design-an-isolated-sharepoint-online-team-site.md)
  
[Soluciones de seguridad](security-solutions.md)

[Implementar un sitio de grupo SharePoint Online aislado](deploy-an-isolated-sharepoint-online-team-site.md)



