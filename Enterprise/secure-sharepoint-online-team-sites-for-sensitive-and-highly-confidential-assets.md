---
title: Proteger los sitios de grupo de SharePoint Online para los activos confidenciales y altamente confidenciales
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 8c088e88-a9ba-4044-bced-722196f4496d
description: 'Resumen: Cómo Contoso implementa protección confidencial y sitios de grupo de SharePoint Online altamente confidenciales para sea más fácil, aún seguro, sus centros de investigación y colaboración para los ejecutivos.'
ms.openlocfilehash: 23511e4156bb04e8bacf970913b00ed36e8ff9c8
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914865"
---
# <a name="secure-sharepoint-online-team-sites-for-sensitive-and-highly-confidential-assets"></a><span data-ttu-id="521e7-103">Proteger los sitios de grupo de SharePoint Online para los activos confidenciales y altamente confidenciales</span><span class="sxs-lookup"><span data-stu-id="521e7-103">Secure SharePoint Online team sites for sensitive and highly confidential assets</span></span>

 <span data-ttu-id="521e7-104">**Resumen:** Cómo Contoso implementada confidencial protección y altamente confidencial SharePoint Online sitios para la colaboración sea más fácil, pero seguro, para los ejecutivos y sus centros de investigación de equipo.</span><span class="sxs-lookup"><span data-stu-id="521e7-104">**Summary:** How Contoso implemented sensitive protection and highly confidential SharePoint Online team sites for easier, yet secure, collaboration for executives and its research centers.</span></span>
  
<span data-ttu-id="521e7-p101">El liderazgo ejecutivo de Contoso se vaya a usar Office 365 y almacenar sus archivos en una sola ubicación para la colaboración, independientemente de donde podría ser un ejecutivo. De forma similar, los departamentos de investigación de Contoso, con divisiones de París, Moscú, Nueva York, Beijing y Bangalore — que le gustaría realizar la transición de sus activos digitales de local a la nube de acceso más fácil y más susceptible de colaboración entre los equipos.</span><span class="sxs-lookup"><span data-stu-id="521e7-p101">The executive leadership of Contoso want to use Office 365 and store their files in a single location for collaboration, regardless of where an executive might be. Similarly, Contoso's research departments—with divisions in Paris, Moscow, New York, Beijing, and Bangalore—would like to transition their on-premises digital assets to the cloud for easier access and more open collaboration across teams.</span></span>
  
<span data-ttu-id="521e7-p102">Sin embargo, en ambos casos, acceso a estos recursos debe estar restringido al subconjunto de personas que tienen permiso para ver o cambiar a ellas, con permisos de curso para los sitios administrados por el personal de TI. Además, incluso si algunos recursos intencionada o no distribuido, deben estar cifradas y tengan permisos para evitar que los usuarios que no tienen acceso para ver o cambiar su contenido.</span><span class="sxs-lookup"><span data-stu-id="521e7-p102">However, in both of these cases, access to these resources must be restricted to the subset of people who are allowed to view or change them, with ongoing permissions for the site administered by IT staff. Additionally, even if some resources are intentionally or unintentionally distributed, they must be encrypted and have permissions to prevent those who do not have access to view or change their contents.</span></span>
  
<span data-ttu-id="521e7-109">Los administradores de seguridad y SharePoint en Contoso del departamento de TI decidido utilizar protección confidencial y sitios de grupo de SharePoint Online altamente confidencial, tal como se muestra en la figura 1.</span><span class="sxs-lookup"><span data-stu-id="521e7-109">Security and SharePoint administrators in Contoso's IT department decided to use sensitive protection and highly-confidential SharePoint Online team sites, as shown in Figure 1.</span></span>
  
<span data-ttu-id="521e7-110">**En la figura 1: Comparación de protección confidencial y sitios de grupo de SharePoint Online altamente confidenciales**</span><span class="sxs-lookup"><span data-stu-id="521e7-110">**Figure 1: Comparison of sensitive protection and highly confidential SharePoint Online team sites**</span></span>

![Protección de información confidencial y sitios de grupo de SharePoint Online muy confidenciales](media/Contoso-Poster/SP-Solution.png)
  
<span data-ttu-id="521e7-112">Contoso utiliza estos pasos para crear sitios de equipo de SharePoint Online seguros para sus los ejecutivos y equipos de investigación:</span><span class="sxs-lookup"><span data-stu-id="521e7-112">Contoso used these steps to create secure SharePoint Online team sites for their executives and research teams:</span></span>
  
1. <span data-ttu-id="521e7-113">Crear un sitio de grupo de SharePoint Online confidencial **ejecutivos**</span><span class="sxs-lookup"><span data-stu-id="521e7-113">Create an **Executives** sensitive SharePoint Online team site</span></span>
    
    <span data-ttu-id="521e7-114">El nuevo sitio de grupo usa grupos de Azure Active Directory (AD) existente para los ejecutivos como miembros con el nivel de permisos de edición de SharePoint y un pequeño conjunto de cuentas de administrador de SharePoint como propietarios con el nivel de permiso Control total.</span><span class="sxs-lookup"><span data-stu-id="521e7-114">The new team site uses existing Azure Active Directory (AD) groups for executives as members with the Edit SharePoint permission level and a small set of SharePoint administrator accounts as owners with the Full Control permission level.</span></span>
    
2. <span data-ttu-id="521e7-115">Migración de archivos de los ejecutivos</span><span class="sxs-lookup"><span data-stu-id="521e7-115">Migrate executives files</span></span>
    
    <span data-ttu-id="521e7-116">Mover local ejecutivo archivos y carpetas existentes para el nuevo sitio de grupo ejecutivos SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="521e7-116">Move existing on-premises executive files and folders to the new Executives SharePoint Online team site.</span></span>
    
3. <span data-ttu-id="521e7-117">Crear un sitio de grupo de SharePoint Online altamente confidencial **investigación**</span><span class="sxs-lookup"><span data-stu-id="521e7-117">Create a **Research** highly confidential SharePoint Online team site</span></span>
    
    <span data-ttu-id="521e7-p103">El nuevo sitio de grupo usa grupos de equipo de investigación de Azure AD existentes como miembros con el nivel de permiso de edición y un pequeño conjunto de cuentas de administrador de SharePoint como propietarios con el nivel de permiso Control total. Una etiqueta AIP asignada a los archivos de la investigación se asegura de que están cifrados y sólo los miembros de un grupo de investigación pueden abrirlos.</span><span class="sxs-lookup"><span data-stu-id="521e7-p103">The new team site uses existing Azure AD research team groups as members with the Edit permission level and a small set of SharePoint administrator accounts as owners with the Full Control permission level. An AIP label assigned to research files ensures that they are encrypted and only members of a research group can open them.</span></span>
    
4. <span data-ttu-id="521e7-120">Migración de archivos de investigación</span><span class="sxs-lookup"><span data-stu-id="521e7-120">Migrate research files</span></span>
    
    <span data-ttu-id="521e7-121">Mover el equipo existente de investigación local archivos y carpetas para el nuevo sitio de grupo investigación SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="521e7-121">Move existing research team on-premises files and folders to the new Research SharePoint Online team site.</span></span>
    
<span data-ttu-id="521e7-p104">El resultado es dos sitios de colaboración cuyo acceso se controla de forma estricta, seguridad y los administradores de SharePoint. Para los archivos con la etiqueta altamente confidencial AIP, incluso si se distribuyen fuera del sitio del equipo de investigación, que se cifran y sólo se pueden abrir mediante un miembro de un equipo de investigación.</span><span class="sxs-lookup"><span data-stu-id="521e7-p104">The result is two collaboration sites whose access is tightly controlled by security and SharePoint administrators. For files with the Highly Confidential AIP label, even if they are distributed outside the Research team site, they are encrypted and can only be opened by a member of a research team.</span></span>
  
<span data-ttu-id="521e7-124">Para obtener más información, vea [archivos y sitios de SharePoint Online seguro](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-and-files).</span><span class="sxs-lookup"><span data-stu-id="521e7-124">For more information, see [Secure SharePoint Online sites and files](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-and-files).</span></span>
  
 <span data-ttu-id="521e7-125">Para definir esta opción para pruebas y desarrollo, prueba de concepto o demostración, vea [sitios de SharePoint Online seguro en un entorno de desarrollo o prueba](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-dev-test).</span><span class="sxs-lookup"><span data-stu-id="521e7-125">To set this up for demonstration, proof-of-concept, or dev/test, see [Secure SharePoint Online sites in a dev/test environment](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-dev-test).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="521e7-126">Vea también</span><span class="sxs-lookup"><span data-stu-id="521e7-126">See Also</span></span>

[<span data-ttu-id="521e7-127">Escenarios empresariales para Contoso Corporation</span><span class="sxs-lookup"><span data-stu-id="521e7-127">Enterprise scenarios for the Contoso Corporation</span></span>](enterprise-scenarios-for-the-contoso-corporation.md)
  
[<span data-ttu-id="521e7-128">Contoso en la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="521e7-128">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="521e7-129">Recursos de arquitectura de TI de la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="521e7-129">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="521e7-130">Stretch Database</span><span class="sxs-lookup"><span data-stu-id="521e7-130">Stretch Database</span></span>](https://msdn.microsoft.com/library/dn935011.aspx)
  
[<span data-ttu-id="521e7-131">Mapa de ruta de Enterprise Cloud de Microsoft: Recursos para los responsables de la toma de decisiones de TI</span><span class="sxs-lookup"><span data-stu-id="521e7-131">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)




