---
title: "Diseñar un sitio de grupo SharePoint Online aislado"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 775a4e9e-3135-4a48-b32f-bbdd9f2bd0aa
description: "Resumen: El paso por el proceso de diseño de sitios de grupo de SharePoint Online aislados."
ms.openlocfilehash: 7b2e8f0bc06a7901c52187ec6e63a056a11fa5e1
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2018
---
# <a name="design-an-isolated-sharepoint-online-team-site"></a><span data-ttu-id="f016e-103">Diseñar un sitio de grupo SharePoint Online aislado</span><span class="sxs-lookup"><span data-stu-id="f016e-103">Design an isolated SharePoint Online team site</span></span>

 <span data-ttu-id="f016e-104">**Resumen:** Paso a través del proceso de diseño de sitios de grupo de SharePoint Online aislados.</span><span class="sxs-lookup"><span data-stu-id="f016e-104">**Summary:** Step through the design process for isolated SharePoint Online team sites.</span></span>
  
<span data-ttu-id="f016e-105">Este artículo le guiará por las decisiones de diseño clave que debe hacer antes de crear un sitio de grupo SharePoint Online aislado.</span><span class="sxs-lookup"><span data-stu-id="f016e-105">This article takes you through the key design decisions you must make before creating an isolated SharePoint Online team site.</span></span>
  
## <a name="phase-1-determine-your-sharepoint-groups-and-permission-levels"></a><span data-ttu-id="f016e-106">Fase 1: Determinar los grupos de SharePoint y los niveles de permisos</span><span class="sxs-lookup"><span data-stu-id="f016e-106">Phase 1: Determine your SharePoint groups and permission levels</span></span>

<span data-ttu-id="f016e-107">Cada sitio de grupo SharePoint Online de forma predeterminada se crea con los siguientes grupos de SharePoint:</span><span class="sxs-lookup"><span data-stu-id="f016e-107">Every SharePoint Online team site by default is created with the following SharePoint groups:</span></span>
  
- <span data-ttu-id="f016e-108">\<nombre del sitio > miembros</span><span class="sxs-lookup"><span data-stu-id="f016e-108">\<site name> Members</span></span>
    
- <span data-ttu-id="f016e-109">\<nombre del sitio > visitantes</span><span class="sxs-lookup"><span data-stu-id="f016e-109">\<site name> Visitors</span></span>
    
- <span data-ttu-id="f016e-110">\<nombre del sitio > propietarios</span><span class="sxs-lookup"><span data-stu-id="f016e-110">\<site name> Owners</span></span>
    
<span data-ttu-id="f016e-111">Estos grupos están separados de los grupos de Office 365 y Azure de Active Directory (AD) y son la base para asignar permisos para los recursos del sitio.</span><span class="sxs-lookup"><span data-stu-id="f016e-111">These groups are separate from Office 365 and Azure Active Directory (AD) groups and are the basis for assigning permissions for the resources of the site.</span></span>
  
<span data-ttu-id="f016e-p101">El conjunto de permisos específicos que determina lo que puede hacer un miembro de un grupo de SharePoint en un sitio es un nivel de permisos. Existen tres niveles de permiso de forma predeterminada para un sitio de grupo SharePoint Online: control total, leer y editar. La siguiente tabla muestra la correlación predeterminado de grupos de SharePoint y los niveles de permisos:</span><span class="sxs-lookup"><span data-stu-id="f016e-p101">The set of specific permissions that determines what a member of a SharePoint group can do in a site is a permission level. There are three permission levels by default for a SharePoint Online team site: Edit, Read, and Full control. The following table shows the default correlation of SharePoint groups and assigned permission levels:</span></span>
  
|<span data-ttu-id="f016e-115">**Grupo de SharePoint**</span><span class="sxs-lookup"><span data-stu-id="f016e-115">**SharePoint group**</span></span>|<span data-ttu-id="f016e-116">**Nivel de permisos**</span><span class="sxs-lookup"><span data-stu-id="f016e-116">**Permission level**</span></span>|
|:-----|:-----|
|<span data-ttu-id="f016e-117">\<nombre del sitio > miembros</span><span class="sxs-lookup"><span data-stu-id="f016e-117">\<site name> Members</span></span>  <br/> |<span data-ttu-id="f016e-118">Editar</span><span class="sxs-lookup"><span data-stu-id="f016e-118">Edit</span></span>  <br/> |
|<span data-ttu-id="f016e-119">\<nombre del sitio > visitantes</span><span class="sxs-lookup"><span data-stu-id="f016e-119">\<site name> Visitors</span></span>  <br/> |<span data-ttu-id="f016e-120">Lectura</span><span class="sxs-lookup"><span data-stu-id="f016e-120">Read</span></span>  <br/> |
|<span data-ttu-id="f016e-121">\<nombre del sitio > propietarios</span><span class="sxs-lookup"><span data-stu-id="f016e-121">\<site name> Owners</span></span>  <br/> |<span data-ttu-id="f016e-122">Control total</span><span class="sxs-lookup"><span data-stu-id="f016e-122">Full control</span></span>  <br/> |
   
 <span data-ttu-id="f016e-p102">**Prácticas recomendadas:** Puede crear grupos de SharePoint adicionales y niveles de permisos. Sin embargo, se recomienda utilizar los niveles de permisos y grupos de SharePoint predeterminados para el sitio de SharePoint Online aislado.</span><span class="sxs-lookup"><span data-stu-id="f016e-p102">**Best practice:** You can create additional SharePoint groups and permission levels. However, we recommend using the default SharePoint groups and permission levels for your isolated SharePoint Online site.</span></span>
  
<span data-ttu-id="f016e-125">Aquí están los niveles de permisos y grupos de SharePoint predeterminados.</span><span class="sxs-lookup"><span data-stu-id="f016e-125">Here are the default SharePoint groups and permission levels.</span></span>
  
![Los grupos y niveles de permisos predeterminados de SharePoint de un sitio de SharePoint Online.](images/3f892ab4-6479-42f0-a505-1ba0ef94b9c6.png)
  
## <a name="phase-2-assign-permissions-to-users-with-access-groups"></a><span data-ttu-id="f016e-127">Fase 2: Asignar permisos a los usuarios con los grupos de acceso</span><span class="sxs-lookup"><span data-stu-id="f016e-127">Phase 2: Assign permissions to users with access groups</span></span>

<span data-ttu-id="f016e-p103">Puede asignar permisos a usuarios agregando su cuenta de usuario o un grupo del que la cuenta de usuario es un miembro, a los grupos de SharePoint de Office 365 o AD Azure. Una vez agregado, las cuentas de usuario de Office 365, ya sea directamente o indirectamente a través de la pertenencia a un grupo de Office 365 o AD Azure, se asigna el nivel de permisos asociado al grupo de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="f016e-p103">You can assign permissions to users by adding their user account, or an Office 365 or Azure AD group of which the user account is a member, to the SharePoint groups. Once added, the Office 365 user accounts, either directly or indirectly via membership in an Office 365 or Azure AD group, are assigned the permission level associated with the SharePoint group.</span></span>
  
<span data-ttu-id="f016e-130">Con los grupos de SharePoint predeterminados como ejemplo:</span><span class="sxs-lookup"><span data-stu-id="f016e-130">Using the default SharePoint groups as an example:</span></span>
  
- <span data-ttu-id="f016e-131">Los miembros de la ** \<nombre del sitio > miembros** grupo de SharePoint, que puede incluir cuentas de usuario y grupos, se asigna el nivel de permisos **Editar**</span><span class="sxs-lookup"><span data-stu-id="f016e-131">Members of the **\<site name> Members** SharePoint group, which can include both user accounts and groups, are assigned the **Edit** permission level</span></span>
    
- <span data-ttu-id="f016e-132">Los miembros de la ** \<nombre del sitio > visitantes** grupo de SharePoint, que puede incluir cuentas de usuario y grupos, se asigna el nivel de permiso de **lectura**</span><span class="sxs-lookup"><span data-stu-id="f016e-132">Members of the **\<site name> Visitors** SharePoint group, which can include both user accounts and groups, are assigned the **Read** permission level</span></span>
    
- <span data-ttu-id="f016e-133">Los miembros de la ** \<nombre del sitio > propietarios** grupo de SharePoint, que puede incluir cuentas de usuario y grupos, se asignan al nivel de permiso **control total**</span><span class="sxs-lookup"><span data-stu-id="f016e-133">Members of the **\<site name> Owners** SharePoint group, which can include both user accounts and groups, are assigned the **Full control** permission level</span></span>
    
 <span data-ttu-id="f016e-p104">**Prácticas recomendadas:** Aunque puede administrar permisos mediante cuentas de usuario individuales, se recomienda utilizar un solo grupo de AD de Azure, conocido como un grupo de acceso, en su lugar. Esto simplifica la administración de permisos a través de la pertenencia al grupo de acceso, en lugar de administrar la lista de los usuarios de cuentas para cada grupo de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="f016e-p104">**Best practice:** Although you can manage permissions through individual user accounts, we recommend that you use a single Azure AD group, known as an access group, instead. This simplifies the management of permissions through membership in the access group, rather than managing the list of user accounts for each SharePoint group.</span></span>
  
<span data-ttu-id="f016e-p105">Azure grupos de AD para Office 365 son diferentes de los grupos de Office 365. Azure grupos AD aparezcan en el centro de administración de Office con su conjunto de **tipo de** **seguridad** y no tienen una dirección de correo electrónico. Los grupos de AD Azure se pueden gestionar:</span><span class="sxs-lookup"><span data-stu-id="f016e-p105">Azure AD groups for Office 365 are different than Office 365 groups. Azure AD groups appear in the Office Admin center with their **Type** set to **Security** and do not have an email address. Azure AD groups can be managed within:</span></span>
  
- <span data-ttu-id="f016e-139">Windows Server Active Directory (AD)</span><span class="sxs-lookup"><span data-stu-id="f016e-139">Windows Server Active Directory (AD)</span></span>
    
    <span data-ttu-id="f016e-p106">Se trata de grupos que se han creado en su infraestructura de AD del servidor de Windows local y sincronizados con la suscripción de Office 365. En el centro de administración de Office, estos grupos tienen un **estado** de **Synched con active directory**.</span><span class="sxs-lookup"><span data-stu-id="f016e-p106">These are groups that have been created in your on-premises Windows Server AD infrastructure and synchronized to your Office 365 subscription. In the Office Admin center, these groups have a **Status** of **Synched with active directory**.</span></span>
    
- <span data-ttu-id="f016e-142">Office 365</span><span class="sxs-lookup"><span data-stu-id="f016e-142">Office 365</span></span>
    
    <span data-ttu-id="f016e-p107">Se trata de grupos que se han creado mediante el centro de administración de Office, el portal de Azure o Microsoft PowerShell. En el centro de administración de Office, estos grupos tienen un **estado** de **la nube**.</span><span class="sxs-lookup"><span data-stu-id="f016e-p107">These are groups that have been created using either the Office Admin center, the Azure portal, or Microsoft PowerShell. In the Office Admin center, these groups have a **Status** of **Cloud**.</span></span>
    
 <span data-ttu-id="f016e-145">**Prácticas recomendadas:** Si está utilizando Windows Server AD local y sincronizar con la suscripción de Office 365, realizar el usuario y administración de grupo con Windows Server AD.</span><span class="sxs-lookup"><span data-stu-id="f016e-145">**Best practice:** If you are using Windows Server AD on-premises and synchronizing with your Office 365 subscription, perform your user and group management with Windows Server AD.</span></span>
  
<span data-ttu-id="f016e-146">Para los sitios de equipo de SharePoint Online aislados, la estructura de grupo recomendado tiene el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="f016e-146">For isolated SharePoint Online team sites, the recommended group structure looks like this:</span></span>
  
|<span data-ttu-id="f016e-147">**Grupo de SharePoint**</span><span class="sxs-lookup"><span data-stu-id="f016e-147">**SharePoint group**</span></span>|<span data-ttu-id="f016e-148">**Grupo de acceso basado en AD de Azure**</span><span class="sxs-lookup"><span data-stu-id="f016e-148">**Azure AD-based access group**</span></span>|<span data-ttu-id="f016e-149">**Nivel de permisos**</span><span class="sxs-lookup"><span data-stu-id="f016e-149">**Permission level**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="f016e-150">\<nombre del sitio > miembros</span><span class="sxs-lookup"><span data-stu-id="f016e-150">\<site name> Members</span></span>  <br/> |<span data-ttu-id="f016e-151">\<nombre del sitio > miembros</span><span class="sxs-lookup"><span data-stu-id="f016e-151">\<site name> Members</span></span>  <br/> |<span data-ttu-id="f016e-152">Editar</span><span class="sxs-lookup"><span data-stu-id="f016e-152">Edit</span></span>  <br/> |
|<span data-ttu-id="f016e-153">\<nombre del sitio > visitantes</span><span class="sxs-lookup"><span data-stu-id="f016e-153">\<site name> Visitors</span></span>  <br/> |<span data-ttu-id="f016e-154">\<nombre del sitio > visores</span><span class="sxs-lookup"><span data-stu-id="f016e-154">\<site name> Viewers</span></span>  <br/> |<span data-ttu-id="f016e-155">Lectura</span><span class="sxs-lookup"><span data-stu-id="f016e-155">Read</span></span>  <br/> |
|<span data-ttu-id="f016e-156">\<nombre del sitio > propietarios</span><span class="sxs-lookup"><span data-stu-id="f016e-156">\<site name> Owners</span></span>  <br/> |<span data-ttu-id="f016e-157">\<nombre del sitio > administradores</span><span class="sxs-lookup"><span data-stu-id="f016e-157">\<site name> Admins</span></span>  <br/> |<span data-ttu-id="f016e-158">Control total</span><span class="sxs-lookup"><span data-stu-id="f016e-158">Full control</span></span>  <br/> |
   
 <span data-ttu-id="f016e-p108">**Prácticas recomendadas:** Aunque puede utilizar Office 365 o AD Azure grupos como miembros de grupos de SharePoint, se recomienda utilizar grupos de AD de Azure. Azure grupos AD, administrados a través de AD del servidor de Windows o de Office 365, proporcionan más flexibilidad para utilizar grupos anidados para asignar permisos.</span><span class="sxs-lookup"><span data-stu-id="f016e-p108">**Best practice:** Although you can use either Office 365 or Azure AD groups as members of SharePoint groups, we recommend that you use Azure AD groups. Azure AD groups, managed either through Windows Server AD or Office 365, give you more flexibility to use nested groups to assign permissions.</span></span>
  
<span data-ttu-id="f016e-161">Aquí es el valor predeterminado configurados para usar grupos de Azure AD-acceso de grupos de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="f016e-161">Here are the default SharePoint groups configured to use Azure AD-based access groups.</span></span>
  
![Uso de grupos de acceso como miembros de grupos de sitio de SharePoint Online predeterminados.](images/50a76328-ae69-483e-9029-ac4e7357b5ef.png)
  
<span data-ttu-id="f016e-163">Al diseñar los grupos de acceso de tres, tenga en cuenta lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="f016e-163">When designing the three access groups, keep the following in mind:</span></span>
  
- <span data-ttu-id="f016e-164">Debería haber sólo unos pocos miembros de la ** \<nombre del sitio > administradores de** grupo de acceso, correspondiente a un número pequeño de administradores de SharePoint Online que están administrando el sitio del equipo.</span><span class="sxs-lookup"><span data-stu-id="f016e-164">There should be only a few members in the **\<site name> Admins** access group, corresponding to a small number of SharePoint Online administrators who are managing the team site.</span></span>
    
- <span data-ttu-id="f016e-p109">La mayoría de los miembros del sitio está en la ** \<nombre del sitio > miembros** o ** \<nombre del sitio > visores** acceder a grupos. Porque sitio los miembros de la ** \<nombre del sitio > miembros** grupo de acceso tienen la capacidad de eliminar o modificar los recursos en el sitio, considere detenidamente su pertenencia al grupo. En caso de duda, agregar el miembro del sitio para la ** \<nombre del sitio > visores** grupo de acceso.</span><span class="sxs-lookup"><span data-stu-id="f016e-p109">Most of your site members are in the **\<site name> Members** or **\<site name> Viewers** access groups. Because site members in the **\<site name> Members** access group have the ability to delete or modify resources in the site, carefully consider its membership. When in doubt, add the site member to the **\<site name> Viewers** access group.</span></span>
    
<span data-ttu-id="f016e-168">Aquí es un ejemplo de los grupos de SharePoint y los grupos de acceso de un sitio aislado denominado ProjectX.</span><span class="sxs-lookup"><span data-stu-id="f016e-168">Here is an example of the SharePoint groups and access groups for an isolated site named ProjectX.</span></span>
  
![Un ejemplo del uso de grupos de acceso de un sitio de SharePoint Online denominado ProjectX.](images/13afe542-9ffd-4671-9f48-210a0e2a502a.png)
  
## <a name="phase-3-use-nested-azure-ad-groups"></a><span data-ttu-id="f016e-170">Fase 3: Uso anidar grupos AD Azure</span><span class="sxs-lookup"><span data-stu-id="f016e-170">Phase 3: Use nested Azure AD groups</span></span>

<span data-ttu-id="f016e-p110">Para un proyecto que se limita a un número reducido de personas, un único nivel de grupos de acceso AD Azure agregado a los grupos de SharePoint del sitio cabrá la mayoría de los escenarios. Sin embargo, si tiene un gran número de personas y a aquellas personas ya miembros de establecidos los grupos AD Azure, más fácilmente puede asignar permisos de SharePoint usando grupos anidados o grupos que contengan otros grupos como miembros.</span><span class="sxs-lookup"><span data-stu-id="f016e-p110">For a project confined to a small number of people, a single level of Azure AD-based access groups added to the SharePoint groups of the site will fit most scenarios. However, if you have a large number of people and those people are already members of established Azure AD groups, you can more easily assign SharePoint permissions by using nested groups, or groups that contain other groups as members.</span></span>
  
<span data-ttu-id="f016e-p111">Por ejemplo, desea crear un sitio de equipo online aislado de SharePoint para la colaboración entre los ejecutivos de ventas, marketing, ingeniería, legal y compatibilidad departamentos y esos ya en sus propios grupos con la cuenta de usuario ejecutivo miembro del grupo. En lugar de crear un nuevo grupo para los nuevos miembros del sitio y colocar las cuentas de usuario individuales de ejecutivo, poner los grupos existentes de ejecutivos para cada departamento en el nuevo grupo.</span><span class="sxs-lookup"><span data-stu-id="f016e-p111">For example, you want to create an isolated SharePoint online team site for collaboration among the executives of the sales, marketing, engineering, legal, and support departments and those departments already their own groups with executive user account membership. Rather than creating a new group for the new site members and placing all the individual executive user accounts in it, put the existing executive groups for each department in the new group.</span></span>
  
 <span data-ttu-id="f016e-p112">Si comparte una suscripción a Office 365 entre varias organizaciones, un solo nivel de pertenencia al grupo de un sitio aislado para una organización podría ser difícil de administrar debido al gran número de cuentas de usuario. En este caso, puede utilizar grupos AD Azure para cada organización que contienen los grupos dentro de sus organizaciones para administrar los permisos anidados.</span><span class="sxs-lookup"><span data-stu-id="f016e-p112">If you are sharing an Office 365 subscription between multiple organizations, a single level of group membership for an isolated site for an organization might become difficult to manage due to the sheer number of user accounts. In this case, you can use nested Azure AD groups for each organization that contain the groups within their organizations to manage the permissions.</span></span>
  
<span data-ttu-id="f016e-177">Para utilizar los grupos de AD Azure anidados:</span><span class="sxs-lookup"><span data-stu-id="f016e-177">To use nested Azure AD groups:</span></span>
  
1. <span data-ttu-id="f016e-178">Identifique o cree los grupos de AD de Azure que contendrá las cuentas de usuario y agregue las cuentas de usuario apropiadas como miembros.</span><span class="sxs-lookup"><span data-stu-id="f016e-178">Identify or create the Azure AD groups that will contain user accounts and add the appropriate user accounts as members.</span></span>
    
2. <span data-ttu-id="f016e-179">Crear el grupo de acceso AD Azure de contenedor que contendrá el resto de los grupos de AD de Azure y agregue como miembros los grupos.</span><span class="sxs-lookup"><span data-stu-id="f016e-179">Create the container Azure AD-based access group that will contain the other Azure AD groups and add those groups as members.</span></span>
    
3.  <span data-ttu-id="f016e-180">Para el nivel de acceso para el grupo de acceso de contenedor adecuado, identifique el grupo de SharePoint y el nivel de permiso correspondiente.</span><span class="sxs-lookup"><span data-stu-id="f016e-180">For the appropriate level of access for the container access group, identify the SharePoint group and corresponding permission level.</span></span>
    
> [!NOTE]
> <span data-ttu-id="f016e-181">No puede utilizar los grupos anidados de Office 365.</span><span class="sxs-lookup"><span data-stu-id="f016e-181">You cannot use nested Office 365 groups.</span></span> 
  
<span data-ttu-id="f016e-182">Aquí es un ejemplo de anuncio de Azure anidado grupos para el grupo de acceso de miembro de ProjectX.</span><span class="sxs-lookup"><span data-stu-id="f016e-182">Here is an example of nested Azure AD groups for the ProjectX member access group.</span></span>
  
![Un ejemplo del uso de los grupos de acceso anidados para el grupo de acceso de los miembros del sitio ProjectX.](images/2abca710-bf9e-4ce8-9bcd-a8e128264fb1.png)
  
<span data-ttu-id="f016e-184">Porque todas las cuentas de usuario en la investigación, la ingeniería y el proyecto conduce equipos pretenden ser integrantes del sitio, es más fácil agregar sus grupos AD Azure al grupo de acceso de los miembros de ProjectX.</span><span class="sxs-lookup"><span data-stu-id="f016e-184">Because all of the user accounts in the Research, Engineering, and Project leads teams are intended to be site members, it is easier to add their Azure AD groups to the ProjectX Members access group.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="f016e-185">Paso siguiente</span><span class="sxs-lookup"><span data-stu-id="f016e-185">Next step</span></span>

<span data-ttu-id="f016e-186">Cuando esté listo para crear y configurar un sitio aislado en producción, vea [implementar un sitio de grupo SharePoint Online aislado](deploy-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="f016e-186">When you are ready to create and configure an isolated site in production, see [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f016e-187">Consulte también</span><span class="sxs-lookup"><span data-stu-id="f016e-187">See Also</span></span>

[<span data-ttu-id="f016e-188">Sitios de equipo de SharePoint Online aislados</span><span class="sxs-lookup"><span data-stu-id="f016e-188">Isolated SharePoint Online team sites</span></span>](isolated-sharepoint-online-team-sites.md)
  
[<span data-ttu-id="f016e-189">Administrar un sitio de grupo SharePoint Online aislado</span><span class="sxs-lookup"><span data-stu-id="f016e-189">Manage an isolated SharePoint Online team site</span></span>](manage-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="f016e-190">Soluciones de seguridad</span><span class="sxs-lookup"><span data-stu-id="f016e-190">Security solutions</span></span>](security-solutions.md)

[<span data-ttu-id="f016e-191">Implementar un sitio de grupo SharePoint Online aislado</span><span class="sxs-lookup"><span data-stu-id="f016e-191">Deploy an isolated SharePoint Online team site</span></span>](deploy-an-isolated-sharepoint-online-team-site.md)



