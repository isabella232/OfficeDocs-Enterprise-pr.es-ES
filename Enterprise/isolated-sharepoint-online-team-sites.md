---
title: Sitios de equipo de SharePoint Online aislados
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: 71250a04-fd2d-4c3c-a32b-b8a838b19a54
description: 'Resumen: Conozca los usos de los sitios de grupo de SharePoint Online aislados.'
ms.openlocfilehash: 358bb16c01c51a76da6557091dacca75e317bf92
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="isolated-sharepoint-online-team-sites"></a><span data-ttu-id="d5702-103">Sitios de equipo de SharePoint Online aislados</span><span class="sxs-lookup"><span data-stu-id="d5702-103">Isolated SharePoint Online team sites</span></span>

 <span data-ttu-id="d5702-104">**Resumen:** Obtenga información sobre los usos de los sitios de grupo de SharePoint Online aislados.</span><span class="sxs-lookup"><span data-stu-id="d5702-104">**Summary:** Learn about the uses for isolated SharePoint Online team sites.</span></span>
  
<span data-ttu-id="d5702-p101">Sitios de equipo de SharePoint Online son una manera fácil de crear rápidamente un espacio de colaboración de notas, documentos, artículos, un calendario y otros recursos de Microsoft Office 365. Sitios de equipo de SharePoint Online están basados en un grupo de Office 365 y tienen un modelo de administración simplificada para permitir una colaboración abierta con un conjunto privado de los miembros del grupo o de toda la organización. Un sitio de grupo de SharePoint Online predeterminada permite a los miembros del grupo Office 365 invitar a otros usuarios y controlar la configuración de permisos.</span><span class="sxs-lookup"><span data-stu-id="d5702-p101">SharePoint Online team sites are an easy way to quickly create a space for collaboration of notes, documents, articles, a calendar, and other resources in Microsoft Office 365. SharePoint Online team sites are based on an Office 365 group and have a simplified administration model to allow open collaboration with a private set of group members or the entire organization. A default SharePoint Online team site allows members of the Office 365 group to invite other users and control permissions settings.</span></span>
  
<span data-ttu-id="d5702-p102">Sin embargo, en algunos casos, desea crear un sitio de grupo SharePoint Online para colaboración donde los permisos de ese sitio están controlados más estrechamente a través de la pertenencia a grupos y niveles de permisos SharePoint Online, que sólo son administrados por SharePoint administradores. Llamamos a esto un sitio aislado, que se aísla en el conjunto de usuarios que están colaborando, ver su contenido o administrar el sitio. Puede que necesite un sitio aislado para lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="d5702-p102">However, in some cases, you want to create a SharePoint Online team site for collaboration where the permissions of that site are more tightly controlled through group membership and SharePoint Online permission levels, which are only managed by SharePoint administrators. We call this an isolated site, which is isolated to the set of users that are either collaborating, viewing its contents, or administering the site. You might need an isolated site for the following:</span></span>
  
- <span data-ttu-id="d5702-111">Un proyecto secreto dentro de su organización.</span><span class="sxs-lookup"><span data-stu-id="d5702-111">A secret project within your organization.</span></span>
    
- <span data-ttu-id="d5702-112">Ubicación muy importantes o valiosa propiedad intelectual de su organización.</span><span class="sxs-lookup"><span data-stu-id="d5702-112">The location for highly-sensitive or valuable intellectual property for your organization.</span></span>
    
- <span data-ttu-id="d5702-113">Los recursos para una acción legal tomada por la organización o a la que se ve sometido.</span><span class="sxs-lookup"><span data-stu-id="d5702-113">The resources for a legal action taken by your organization or that to which it is being subjected.</span></span>
    
- <span data-ttu-id="d5702-114">Compartir una suscripción a Office 365 entre varias organizaciones que dispone de algunos se superponen, pero la mayor parte existen como entidades de negocio independientes.</span><span class="sxs-lookup"><span data-stu-id="d5702-114">To share an Office 365 subscription between multiple organizations that have some overlap, but for the most part exist as separate business entities.</span></span>
    
<span data-ttu-id="d5702-115">Aquí están los requisitos de un sitio aislado:</span><span class="sxs-lookup"><span data-stu-id="d5702-115">Here are the requirements of an isolated site:</span></span>
  
- <span data-ttu-id="d5702-116">Sólo los administradores de SharePoint Online pueden realizar la administración del sitio, que incluye la pertenencia al grupo de acceso al sitio y la configuración de permisos personalizados.</span><span class="sxs-lookup"><span data-stu-id="d5702-116">Only SharePoint Online administrators can perform site administration, which includes group membership for access to the site and configuring custom permissions.</span></span>
    
- <span data-ttu-id="d5702-117">Los miembros del sitio no pueden invitar a otros miembros al sitio del grupo.</span><span class="sxs-lookup"><span data-stu-id="d5702-117">Members of the site cannot invite other members to the team site.</span></span>
    
- <span data-ttu-id="d5702-p103">Los usuarios que no son miembros del sitio aislado no pueden solicitar acceso al sitio. Recibirán un acceso denegado página web cuando intentan tener acceso a cualquier dirección URL asociada con el sitio.</span><span class="sxs-lookup"><span data-stu-id="d5702-p103">Users who are not members of the isolated site cannot request access to the site. They will receive an access denied web page when they attempt to access any URL associated with the site.</span></span>
    
<span data-ttu-id="d5702-p104">La desventaja de que requieren permisos personalizados por los administradores de SharePoint Online y control de acceso centralizado es que el sitio permanece aislado en el tiempo. Por ejemplo, miembros actuales no pueden, ya sea intencionada o accidentalmente, invitar o configurar permisos personalizados a otros usuarios de la suscripción de Office 365 que no sean miembros del sitio.</span><span class="sxs-lookup"><span data-stu-id="d5702-p104">The tradeoff of requiring centralized access control and custom permissions by SharePoint Online administrators is that the site remains isolated over time. For example, current members cannot, either intentionally or accidentally, invite or configure custom permissions for other users within the Office 365 subscription who should not be members of the site.</span></span>
  
<span data-ttu-id="d5702-122">Un sitio aislado puede utilizarse con otras características, tales como:</span><span class="sxs-lookup"><span data-stu-id="d5702-122">An isolated site can be used with other features, such as:</span></span>
  
- <span data-ttu-id="d5702-123">Information Rights Management para asegurar que los recursos en el sitio permanecen cifrados, incluso si se descargan localmente y cargar a otro sitio que esté disponible para toda la organización.</span><span class="sxs-lookup"><span data-stu-id="d5702-123">Information Rights Management to ensure that the resources on the site remain encrypted, even if they are downloaded locally and uploaded to another site that is available to the entire organization.</span></span>
    
- <span data-ttu-id="d5702-124">Prevención de pérdida de datos para evitar que los usuarios envíen los recursos del sitio, como los archivos de correo electrónico.</span><span class="sxs-lookup"><span data-stu-id="d5702-124">Data loss prevention to prevent users from sending the resources of the site, such as files, in email.</span></span>
    
## <a name="next-steps"></a><span data-ttu-id="d5702-125">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="d5702-125">Next steps</span></span>

<span data-ttu-id="d5702-126">Para probar un sitio de grupo de SharePoint Online aislado en una suscripción de prueba, consulte las instrucciones paso a paso en el [entorno de pruebas y desarrollo de sitio de equipo aislado de SharePoint Online](isolated-sharepoint-online-team-site-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="d5702-126">To try out an isolated SharePoint Online team site in a trial subscription, see the step-by-step instructions in [Isolated SharePoint Online team site dev/test environment](isolated-sharepoint-online-team-site-dev-test-environment.md).</span></span>
  
<span data-ttu-id="d5702-127">Cuando esté listo para implementar un sitio de equipo de SharePoint Online aislado de producción, consulte las consideraciones de diseño paso a paso en el [Diseño de un sitio de grupo SharePoint Online aislado](design-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="d5702-127">When you are ready to deploy an isolated SharePoint Online team site in production, see the step-by-step design considerations in [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d5702-128">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d5702-128">See Also</span></span>

[<span data-ttu-id="d5702-129">Diseñar un sitio de grupo SharePoint Online aislado</span><span class="sxs-lookup"><span data-stu-id="d5702-129">Design an isolated SharePoint Online team site</span></span>](design-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="d5702-130">Administrar un sitio de grupo SharePoint Online aislado</span><span class="sxs-lookup"><span data-stu-id="d5702-130">Manage an isolated SharePoint Online team site</span></span>](manage-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="d5702-131">Soluciones de seguridad</span><span class="sxs-lookup"><span data-stu-id="d5702-131">Security solutions</span></span>](security-solutions.md)

[<span data-ttu-id="d5702-132">Implementar un sitio de grupo SharePoint Online aislado</span><span class="sxs-lookup"><span data-stu-id="d5702-132">Deploy an isolated SharePoint Online team site</span></span>](deploy-an-isolated-sharepoint-online-team-site.md)


