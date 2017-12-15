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
# <a name="manage-an-isolated-sharepoint-online-team-site"></a><span data-ttu-id="52b60-103">Administrar un sitio de grupo SharePoint Online aislado</span><span class="sxs-lookup"><span data-stu-id="52b60-103">Manage an isolated SharePoint Online team site</span></span>

 <span data-ttu-id="52b60-104">**Resumen:** Administrar el sitio SharePoint Online del grupo aislado con estos procedimientos.</span><span class="sxs-lookup"><span data-stu-id="52b60-104">**Summary:** Manage your isolated SharePoint Online team site with these procedures.</span></span>
  
<span data-ttu-id="52b60-105">Este artículo describe las operaciones comunes de administración de un sitio de grupo SharePoint Online aislado.</span><span class="sxs-lookup"><span data-stu-id="52b60-105">This article describes common management operations for an isolated SharePoint Online team site.</span></span>
  
## <a name="add-a-new-user"></a><span data-ttu-id="52b60-106">Agregar un nuevo usuario</span><span class="sxs-lookup"><span data-stu-id="52b60-106">Add a new user</span></span>

<span data-ttu-id="52b60-107">Cuando alguien nuevo une al sitio, debe decidir su nivel de participación en el sitio:</span><span class="sxs-lookup"><span data-stu-id="52b60-107">When someone new joins the site, you must decide their level of participation in the site:</span></span>
  
- <span data-ttu-id="52b60-108">Administración: Agregue la nueva cuenta de usuario para el sitio de grupo de acceso de administradores</span><span class="sxs-lookup"><span data-stu-id="52b60-108">Administration: Add the new user account to the site admins access group</span></span>
    
- <span data-ttu-id="52b60-109">Colaboración activa: agregar la cuenta de usuario para el sitio de grupo de acceso a miembros</span><span class="sxs-lookup"><span data-stu-id="52b60-109">Active collaboration: Add the user account to the site members access group</span></span>
    
- <span data-ttu-id="52b60-110">Ver: Agregar la cuenta de usuario en el sitio los participantes ver grupo</span><span class="sxs-lookup"><span data-stu-id="52b60-110">Viewing: Add the user account to the site viewers access group</span></span>
    
<span data-ttu-id="52b60-111">Si está administrando cuentas de usuario y grupos a través de servidor de Active Directory (AD) de Windows, agregue los usuarios adecuados a los grupos de acceso apropiado mediante sus normal Windows Server AD usuario y grupo de procedimientos de gestión y espere a que la sincronización con su Suscripción de Office 365.</span><span class="sxs-lookup"><span data-stu-id="52b60-111">If you are managing user accounts and groups through Windows Server Active Directory (AD), add the appropriate users to the appropriate access groups using your normal Windows Server AD user and group management procedures and wait for synchronization with your Office 365 subscription.</span></span>
  
<span data-ttu-id="52b60-112">Si está administrando cuentas de usuario y grupos mediante Office 365, puede utilizar el centro de administración de Office o Microsoft PowerShell:</span><span class="sxs-lookup"><span data-stu-id="52b60-112">If you are managing user accounts and groups through Office 365, you can use the Office Admin center or Microsoft PowerShell:</span></span>
  
- <span data-ttu-id="52b60-113">Para el centro de administración de Office, inicie sesión con una cuenta de usuario que se ha asignado la función de administrador de la cuenta de usuario o administrador de la empresa y usar grupos para agregar los usuarios adecuados a los grupos de acceso apropiado.</span><span class="sxs-lookup"><span data-stu-id="52b60-113">For the Office Admin center, sign in with a user account that has been assigned the User Account Administrator or Company Administrator role and use Groups to add the appropriate users to the appropriate access groups.</span></span>
    
- <span data-ttu-id="52b60-p101">Para PowerShell, primero [conecte con el módulo de Active Directory V2 PowerShell de Azure](https://go.microsoft.com/fwlink/?linkid=842218). Para agregar una cuenta de usuario a un grupo de acceso mediante su nombre principal de usuario (UPN), utilice el siguiente bloque de comandos de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="52b60-p101">For PowerShell, first [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218). To add a user account to an access group with its user principal name (UPN), use the following PowerShell command block:</span></span>
    
```
$userUPN="<UPN of the user account>"
$grpName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

> [!TIP]
> <span data-ttu-id="52b60-116">Para un archivo de texto que contiene todos los comandos de PowerShell y un Excel hoja de trabajo de configuración que genera comandos de PowerShell basándose en su grupo y usuario nombres de cuenta, descargue el [Aislado SharePoint Online sitio Deployment Kit de equipo](https://gallery.technet.microsoft.com/Isolated-SharePoint-Online-0b364907).</span><span class="sxs-lookup"><span data-stu-id="52b60-116">For a text file that contains all the PowerShell commands and an Excel configuration worksheet that generates PowerShell commands based on your group and user account names, download the [Isolated SharePoint Online Team Site Deployment Kit](https://gallery.technet.microsoft.com/Isolated-SharePoint-Online-0b364907).</span></span> 

<span data-ttu-id="52b60-117">Para agregar una cuenta de usuario a un grupo de acceso con su nombre para mostrar, utilice el siguiente bloque de comandos de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="52b60-117">To add a user account to an access group with its display name, use the following PowerShell command block:</span></span>

```
$userDisplayName="<display name of the user account>"
$grpName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userDisplayName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

## <a name="add-a-new-group"></a><span data-ttu-id="52b60-118">Agregar un nuevo grupo</span><span class="sxs-lookup"><span data-stu-id="52b60-118">Add a new group</span></span>

<span data-ttu-id="52b60-119">Para obtener acceso a todo un grupo, debe decidir el nivel de la participación de todos los miembros del grupo en el sitio:</span><span class="sxs-lookup"><span data-stu-id="52b60-119">To add access to an entire group, you must decide the level of participation of all the members of the group in the site:</span></span>
  
- <span data-ttu-id="52b60-120">Administración: Agregar el grupo al sitio de grupo de acceso de administradores</span><span class="sxs-lookup"><span data-stu-id="52b60-120">Administration: Add the group to the site admins access group</span></span>
    
- <span data-ttu-id="52b60-121">Colaboración activa: agregar el grupo al sitio de grupo de acceso a miembros</span><span class="sxs-lookup"><span data-stu-id="52b60-121">Active collaboration: Add the group to the site members access group</span></span>
    
- <span data-ttu-id="52b60-122">Ver: Agregar el grupo al sitio visores acceder a grupo</span><span class="sxs-lookup"><span data-stu-id="52b60-122">Viewing: Add the group to the site viewers access group</span></span>
    
<span data-ttu-id="52b60-123">Si está administrando cuentas de usuario y grupos de AD del servidor de Windows, agregar los grupos correspondientes a los grupos apropiados con su usuario de AD del servidor Windows normal y procedimientos de administración de grupo y espere a que la sincronización con su suscripción de Office 365.</span><span class="sxs-lookup"><span data-stu-id="52b60-123">If you are managing user accounts and groups through Windows Server AD, add the appropriate groups to the appropriate groups using your normal Windows Server AD user and group management procedures and wait for synchronization with your Office 365 subscription.</span></span>
  
<span data-ttu-id="52b60-124">Si está administrando cuentas de usuario y grupos mediante Office 365, puede utilizar el centro de administración de Office o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="52b60-124">If you are managing user accounts and groups through Office 365, you can use the Office Admin center or PowerShell:</span></span>
  
- <span data-ttu-id="52b60-125">Para el centro de administración de Office, inicie sesión con una cuenta de usuario que se ha asignado la función de administrador de la cuenta de usuario o administrador de la empresa y usar grupos para agregar los grupos correspondientes a los grupos de acceso apropiado.</span><span class="sxs-lookup"><span data-stu-id="52b60-125">For the Office Admin center, sign in with a user account that has been assigned the User Account Administrator or Company Administrator role and use Groups to add the appropriate groups to the appropriate access groups.</span></span>
    
- <span data-ttu-id="52b60-p102">Para PowerShell, primero [conecte con el módulo de Active Directory V2 PowerShell de Azure](https://go.microsoft.com/fwlink/?linkid=842218). A continuación, utilice los siguientes comandos de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="52b60-p102">For PowerShell, first [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218). Then, use the following PowerShell commands:</span></span>
 
```
$newGroupName="<display name of the new group to add>"
$siteGrpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $newGroupName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $siteGrpName }).ObjectID
```

## <a name="remove-a-user"></a><span data-ttu-id="52b60-128">Quitar un usuario</span><span class="sxs-lookup"><span data-stu-id="52b60-128">Remove a user</span></span>

<span data-ttu-id="52b60-129">Cuando el acceso de un usuario debe quitarse del sitio, se eliminen en el grupo de acceso de las que actualmente son un miembro basado en su participación en el sitio:</span><span class="sxs-lookup"><span data-stu-id="52b60-129">When someone's access must be removed from the site, you remove them from the access group for which they are currently a member based on their participation in the site:</span></span>
  
- <span data-ttu-id="52b60-130">Administración: Quitar la cuenta de usuario del grupo de acceso de administradores de sitio</span><span class="sxs-lookup"><span data-stu-id="52b60-130">Administration: Remove the user account from the site admins access group</span></span>
    
- <span data-ttu-id="52b60-131">Colaboración activa: quitar la cuenta de usuario del grupo de acceso de los miembros de sitio</span><span class="sxs-lookup"><span data-stu-id="52b60-131">Active collaboration: Remove the user account from the site members access group</span></span>
    
- <span data-ttu-id="52b60-132">Visualización: Quitar la cuenta de usuario del grupo de acceso de sitio visores</span><span class="sxs-lookup"><span data-stu-id="52b60-132">Viewing: Remove the user account from the site viewers access group</span></span>
    
<span data-ttu-id="52b60-133">Si está administrando cuentas de usuario y grupos de AD del servidor de Windows, quitar los usuarios adecuados de los grupos de acceso apropiada con su usuario de AD del servidor Windows normal y procedimientos de administración de grupo y espere a que la sincronización con el Office 365 suscripción.</span><span class="sxs-lookup"><span data-stu-id="52b60-133">If you are managing user accounts and groups through Windows Server AD, remove the appropriate users from the appropriate access groups using your normal Windows Server AD user and group management procedures and wait for synchronization with your Office 365 subscription.</span></span>
  
<span data-ttu-id="52b60-134">Si está administrando cuentas de usuario y grupos mediante Office 365, puede utilizar el centro de administración de Office o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="52b60-134">If you are managing user accounts and groups through Office 365, you can use the Office Admin center or PowerShell:</span></span>
  
- <span data-ttu-id="52b60-135">Para el centro de administración de Office, inicie sesión con una cuenta de usuario que se ha asignado la función de administrador de la cuenta de usuario o administrador de la empresa y utilizar grupos para quitar los usuarios adecuados de los grupos de acceso apropiado.</span><span class="sxs-lookup"><span data-stu-id="52b60-135">For the Office Admin center, sign in with a user account that has been assigned the User Account Administrator or Company Administrator role and use Groups to remove the appropriate users from the appropriate access groups.</span></span>
    
- <span data-ttu-id="52b60-p103">Para PowerShell, primero [conecte con el módulo de Active Directory V2 PowerShell de Azure](https://go.microsoft.com/fwlink/?linkid=842218). Para quitar una cuenta de usuario de un grupo de acceso con su UPN, utilice el siguiente bloque de comandos de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="52b60-p103">For PowerShell, first [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218). To remove a user account from an access group with its UPN, use the following PowerShell command block:</span></span>
    
```
$userUPN="<UPN of the user account>"
$grpName="<display name of the access group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

<span data-ttu-id="52b60-138">Para quitar una cuenta de usuario de un grupo de acceso con su nombre para mostrar, utilice el siguiente bloque de comandos de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="52b60-138">To remove a user account from an access group with its display name, use the following PowerShell command block:</span></span>
    
```
$userDisplayName="<display name of the user account>"
$grpName="<display name of the access group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userDisplayName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

## <a name="remove-a-group"></a><span data-ttu-id="52b60-139">Quitar un grupo</span><span class="sxs-lookup"><span data-stu-id="52b60-139">Remove a group</span></span>

<span data-ttu-id="52b60-140">Para quitar el acceso de un grupo entero, quita el grupo desde el grupo de acceso de las que actualmente son un miembro basado en su participación en el sitio:</span><span class="sxs-lookup"><span data-stu-id="52b60-140">To remove access for an entire group, you remove the group from the access group for which they are currently a member based on their participation in the site:</span></span>
  
- <span data-ttu-id="52b60-141">Administración: Quitar el grupo desde el grupo de acceso de administradores de sitio</span><span class="sxs-lookup"><span data-stu-id="52b60-141">Administration: Remove the group from the site admins access group</span></span>
    
- <span data-ttu-id="52b60-142">Colaboración activa: quitar el grupo de grupo de acceso de miembros del sitio</span><span class="sxs-lookup"><span data-stu-id="52b60-142">Active collaboration: Remove the group from the site members access group</span></span>
    
- <span data-ttu-id="52b60-143">Visualización: Quitar el grupo desde el grupo de acceso de sitio visores</span><span class="sxs-lookup"><span data-stu-id="52b60-143">Viewing: Remove the group from the site viewers access group</span></span>
    
<span data-ttu-id="52b60-144">Si está administrando cuentas de usuario y grupos de Active Directory de Windows Server, quite los grupos correspondientes de los grupos de acceso apropiado mediante sus normal Windows Server AD usuario y grupo de procedimientos de administración y espere a que la sincronización con su Suscripción de Office 365.</span><span class="sxs-lookup"><span data-stu-id="52b60-144">If you are managing user accounts and groups through Windows Server Active Directory, remove the appropriate groups from the appropriate access groups using your normal Windows Server AD user and group management procedures and wait for synchronization with your Office 365 subscription.</span></span>
  
<span data-ttu-id="52b60-145">Si está administrando cuentas de usuario y grupos mediante Office 365, puede utilizar el centro de administración de Office o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="52b60-145">If you are managing user accounts and groups through Office 365, you can use the Office Admin center or PowerShell:</span></span>
  
- <span data-ttu-id="52b60-146">Para el centro de administración de Office, inicie sesión con una cuenta de usuario que se ha asignado la función de administrador de la cuenta de usuario o administrador de la empresa y utilizar grupos para quitar los grupos correspondientes de los grupos de acceso apropiado.</span><span class="sxs-lookup"><span data-stu-id="52b60-146">For the Office Admin center, sign in with a user account that has been assigned the User Account Administrator or Company Administrator role and use Groups to remove the appropriate groups from the appropriate access groups.</span></span>
    
- <span data-ttu-id="52b60-147">Para PowerShell, primero [conecte con el módulo de Active Directory V2 PowerShell de Azure](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="52b60-147">For PowerShell, first [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>    
<span data-ttu-id="52b60-148">Para quitar un grupo de un grupo de acceso utilizando sus nombres para mostrar, utilice el siguiente bloque de comandos de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="52b60-148">To remove a group from an access group using their display names, use the following PowerShell command block:</span></span>
    
```
$groupMemberName="<display name of the group to remove>"
$grpName="<display name of the access group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

## <a name="create-a-documents-subfolder-with-custom-permissions"></a><span data-ttu-id="52b60-149">Crear una subcarpeta en documentos con permisos personalizados</span><span class="sxs-lookup"><span data-stu-id="52b60-149">Create a documents subfolder with custom permissions</span></span>

<span data-ttu-id="52b60-p104">En algunos casos, un subconjunto de las personas que trabajan en el sitio aislado necesita un lugar más privado para colaborar. Para los sitios de SharePoint Online, puede crear una subcarpeta en la carpeta de documentos del sitio y asignar permisos personalizados. Los que no tienen permisos no podrán ver la subcarpeta.</span><span class="sxs-lookup"><span data-stu-id="52b60-p104">In some cases, a subset of the people working within the isolated site need a more private place to collaborate. For SharePoint Online sites, you can create a subfolder in the Documents folder of the site and assign custom permissions. Those without permissions will not see the subfolder.</span></span>
  
<span data-ttu-id="52b60-153">Para crear una subcarpeta en documentos con permisos personalizados, siga este procedimiento:</span><span class="sxs-lookup"><span data-stu-id="52b60-153">To create a documents subfolder with custom permissions, do the following:</span></span>
  
1. <span data-ttu-id="52b60-p105">Iniciar sesión en Office 365 con una cuenta que sea miembro del grupo Administradores de acceso para el sitio. Para obtener ayuda, visite [dónde puede iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="52b60-p105">Sign in to Office 365 with an account that is a member of the admins access group for the site. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="52b60-156">Ir al sitio del grupo aislado y haga clic en **documentos**.</span><span class="sxs-lookup"><span data-stu-id="52b60-156">Go to the isolated team site and click **Documents**.</span></span>
    
3. <span data-ttu-id="52b60-157">Vaya a la carpeta en la carpeta de documentos que contendrá la subcarpeta con permisos personalizados, cree la carpeta y, a continuación, ábralo.</span><span class="sxs-lookup"><span data-stu-id="52b60-157">Browse to the folder in the documents folder that will contain the subfolder with custom permissions, create the folder, and then open it.</span></span>
    
4. <span data-ttu-id="52b60-158">Haga clic en **Compartir**.</span><span class="sxs-lookup"><span data-stu-id="52b60-158">Click **Share**.</span></span>
    
5. <span data-ttu-id="52b60-159">Haga clic en **compartido con > avanzada**.</span><span class="sxs-lookup"><span data-stu-id="52b60-159">Click **Shared with > Advanced**.</span></span>
    
6. <span data-ttu-id="52b60-160">Haga clic en **Detener la herencia de permisos**y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="52b60-160">Click **Stop inheriting permissions**, and then click **OK**.</span></span>
    
7. <span data-ttu-id="52b60-161">Haga clic en **Compartir**.</span><span class="sxs-lookup"><span data-stu-id="52b60-161">Click **Share**.</span></span>
    
8. <span data-ttu-id="52b60-162">Haga clic en **compartido con > avanzada**.</span><span class="sxs-lookup"><span data-stu-id="52b60-162">Click **Shared with > Advanced**.</span></span>
    
9. <span data-ttu-id="52b60-163">Haga clic en **conceder permisos > compartido con > avanzada**.</span><span class="sxs-lookup"><span data-stu-id="52b60-163">Click **Grant Permissions > Shared with > Advanced**.</span></span>
    
10. <span data-ttu-id="52b60-164">En la página permisos, haga clic en ** \<nombre del sitio > integrantes de la lista**.</span><span class="sxs-lookup"><span data-stu-id="52b60-164">On the permissions page, click **\<site name> Members in the list**.</span></span>
    
11. <span data-ttu-id="52b60-165">En la ** \<nombre del sitio > miembros** de página, seleccione la marca de verificación junto a grupo de acceso de miembros del sitio, haga clic en **acciones**, haga clic en **quitar usuarios del grupo**y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="52b60-165">On the **\<site name> Members** page, select the checkmark next to the site members access group, click **Actions**, click **Remove users from group**, and then click **OK**.</span></span>
    
12. <span data-ttu-id="52b60-166">Para agregar los miembros específicos para esta subcarpeta, haga clic en **Nuevo > Agregar usuarios**.</span><span class="sxs-lookup"><span data-stu-id="52b60-166">To add specific members to this subfolder, click **New > Add users**.</span></span>
    
13. <span data-ttu-id="52b60-167">En el cuadro de diálogo **Compartir** , escriba los nombres de las cuentas de usuario que pueden colaborar en los archivos de la subcarpeta y, a continuación, haga clic en **Compartir**.</span><span class="sxs-lookup"><span data-stu-id="52b60-167">In the **Share** dialog box, type the names of the user accounts that can collaborate on files in the subfolder, and then click **Share**.</span></span>
    
14. <span data-ttu-id="52b60-168">Actualizar la página web para ver los nuevos resultados.</span><span class="sxs-lookup"><span data-stu-id="52b60-168">Refresh the web page to see the new results.</span></span>
    
15. <span data-ttu-id="52b60-169">En **los grupos** en la exploración de la izquierda, haga clic en el ** \<nombre del sitio > visitantes** grupo y siga los pasos del 11 al 14 para especificar el conjunto de cuentas de usuario que puede ver los archivos en la subcarpeta (según sea necesario).</span><span class="sxs-lookup"><span data-stu-id="52b60-169">Under **Groups** in the left navigation, click the **\<site name> Visitors** group and use steps 11-14 to specify the set of user accounts that can view the files in the subfolder (as needed).</span></span>
    
16. <span data-ttu-id="52b60-170">En **los grupos** en la exploración de la izquierda, haga clic en el ** \<nombre del sitio > propietarios** grupo y siga los pasos del 11 al 14 para especificar el conjunto de cuentas de usuario que puede administrar los permisos en la subcarpeta (según sea necesario).</span><span class="sxs-lookup"><span data-stu-id="52b60-170">Under **Groups** in the left navigation, click the **\<site name> Owners** group and use steps 11-14 to specify the set of user accounts that can administer the permissions in the subfolder (as needed).</span></span>
    
17. <span data-ttu-id="52b60-171">Cierre la ficha **personas y grupos** en el explorador.</span><span class="sxs-lookup"><span data-stu-id="52b60-171">Close the **People and Groups** tab in your browser.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="52b60-172">See Also</span><span class="sxs-lookup"><span data-stu-id="52b60-172">See Also</span></span>

[<span data-ttu-id="52b60-173">Sitios de equipo de SharePoint Online aislados</span><span class="sxs-lookup"><span data-stu-id="52b60-173">Isolated SharePoint Online team sites</span></span>](isolated-sharepoint-online-team-sites.md)
  
[<span data-ttu-id="52b60-174">Diseñar un sitio de grupo SharePoint Online aislado</span><span class="sxs-lookup"><span data-stu-id="52b60-174">Design an isolated SharePoint Online team site</span></span>](design-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="52b60-175">Soluciones de seguridad</span><span class="sxs-lookup"><span data-stu-id="52b60-175">Security solutions</span></span>](security-solutions.md)

[<span data-ttu-id="52b60-176">Implementar un sitio de grupo SharePoint Online aislado</span><span class="sxs-lookup"><span data-stu-id="52b60-176">Deploy an isolated SharePoint Online team site</span></span>](deploy-an-isolated-sharepoint-online-team-site.md)



