---
title: Sitios de equipo SharePoint Online seguros de activos importantes y altamente confidenciales
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 8c088e88-a9ba-4044-bced-722196f4496d
description: "Resumen: Cómo Contoso implementa protección sensible y sitios de grupo de SharePoint Online altamente confidenciales para más fácil, aún seguro, sus centros de investigación y colaboración para los ejecutivos."
ms.openlocfilehash: c615280d39117f68515fb13d4ba83428d73e4fd3
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="secure-sharepoint-online-team-sites-for-sensitive-and-highly-confidential-assets"></a><span data-ttu-id="8d36f-103">Sitios de equipo SharePoint Online seguros de activos importantes y altamente confidenciales</span><span class="sxs-lookup"><span data-stu-id="8d36f-103">Secure SharePoint Online team sites for sensitive and highly confidential assets</span></span>

 <span data-ttu-id="8d36f-104">**Resumen:** Cómo Contoso implementa confidencial protección y altamente confidencial SharePoint Online sitios para la colaboración más fácil y segura, para ejecutivos y sus centros de investigación del equipo.</span><span class="sxs-lookup"><span data-stu-id="8d36f-104">**Summary:** How Contoso implemented sensitive protection and highly confidential SharePoint Online team sites for easier, yet secure, collaboration for executives and its research centers.</span></span>
  
<span data-ttu-id="8d36f-p101">El liderazgo ejecutivo de Contoso desea utilizar Office 365 y almacenar sus archivos en una única ubicación para colaboración, independientemente de dónde podría ser un ejecutivo. De forma similar, los departamentos de investigación de Contoso, con divisiones en Bangalore, Beijing, Moscú, Nueva York y París — le gustaría sus activos digitales de local a la nube para facilitar el acceso y la colaboración más abierta la transición entre equipos.</span><span class="sxs-lookup"><span data-stu-id="8d36f-p101">The executive leadership of Contoso want to use Office 365 and store their files in a single location for collaboration, regardless of where an executive might be. Similarly, Contoso's research departments—with divisions in Paris, Moscow, New York, Beijing, and Bangalore—would like to transition their on-premises digital assets to the cloud for easier access and more open collaboration across teams.</span></span>
  
<span data-ttu-id="8d36f-p102">Sin embargo, en ambos casos, el acceso a estos recursos debe restringirse al subconjunto de personas que pueden ver o modificarlas, con continua permisos para el sitio administrado por el personal de TI. Además, incluso si algunos recursos de forma intencionada o no distribuidas, deben estar cifrados y tienen permisos para impedir que quienes no tienen acceso para ver o cambiar su contenido.</span><span class="sxs-lookup"><span data-stu-id="8d36f-p102">However, in both of these cases, access to these resources must be restricted to the subset of people who are allowed to view or change them, with ongoing permissions for the site administered by IT staff. Additionally, even if some resources are intentionally or unintentionally distributed, they must be encrypted and have permissions to prevent those who do not have access to view or change their contents.</span></span>
  
<span data-ttu-id="8d36f-109">Los administradores de seguridad y SharePoint en Contoso del departamento de TI decidió utilizar protección sensible y sitios de grupo de SharePoint Online altamente confidencial, como se muestra en la figura 1.</span><span class="sxs-lookup"><span data-stu-id="8d36f-109">Security and SharePoint administrators in Contoso's IT department decided to use sensitive protection and highly-confidential SharePoint Online team sites, as shown in Figure 1.</span></span>
  
<span data-ttu-id="8d36f-110">**Figura 1: Comparación de protección sensible y altamente confidenciales sitios de grupo de SharePoint Online**</span><span class="sxs-lookup"><span data-stu-id="8d36f-110">**Figure 1: Comparison of sensitive protection and highly confidential SharePoint Online team sites**</span></span>

![Protección de información confidencial y sitios de grupo de SharePoint Online muy confidenciales](images/Contoso_Poster/SP_Solution.png)
  
<span data-ttu-id="8d36f-112">Contoso utiliza estos pasos para crear sitios de equipo de SharePoint Online seguros para sus ejecutivos y equipos de investigación:</span><span class="sxs-lookup"><span data-stu-id="8d36f-112">Contoso used these steps to create secure SharePoint Online team sites for their executives and research teams:</span></span>
  
1. <span data-ttu-id="8d36f-113">Crear un sitio de grupo de SharePoint Online confidencial **ejecutivos**</span><span class="sxs-lookup"><span data-stu-id="8d36f-113">Create an **Executives** sensitive SharePoint Online team site</span></span>
    
    <span data-ttu-id="8d36f-114">El nuevo sitio de equipo utiliza los grupos existentes de Azure de Active Directory (AD) para ejecutivos como miembros con el nivel de permisos de SharePoint Editar y un pequeño conjunto de cuentas de administrador de SharePoint como propietarios con el nivel de permiso Control total.</span><span class="sxs-lookup"><span data-stu-id="8d36f-114">The new team site uses existing Azure Active Directory (AD) groups for executives as members with the Edit SharePoint permission level and a small set of SharePoint administrator accounts as owners with the Full Control permission level.</span></span>
    
2. <span data-ttu-id="8d36f-115">Migrar archivos de ejecutivos</span><span class="sxs-lookup"><span data-stu-id="8d36f-115">Migrate executives files</span></span>
    
    <span data-ttu-id="8d36f-116">Mover local ejecutivo archivos y carpetas existentes en el nuevo sitio del grupo ejecutivos SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="8d36f-116">Move existing on-premises executive files and folders to the new Executives SharePoint Online team site.</span></span>
    
3. <span data-ttu-id="8d36f-117">Crear un sitio de grupo de SharePoint Online altamente confidencial **investigación**</span><span class="sxs-lookup"><span data-stu-id="8d36f-117">Create a **Research** highly confidential SharePoint Online team site</span></span>
    
    <span data-ttu-id="8d36f-p103">El nuevo sitio de equipo utiliza grupos de equipo de investigación de Azure AD existentes como miembros con el nivel de permiso de edición y un pequeño conjunto de cuentas de administrador de SharePoint como propietarios con el nivel de permiso Control total. Una etiqueta AIP asignada a archivos de investigación garantiza que están cifrados y sólo los miembros de un grupo de investigación pueden abrirlos.</span><span class="sxs-lookup"><span data-stu-id="8d36f-p103">The new team site uses existing Azure AD research team groups as members with the Edit permission level and a small set of SharePoint administrator accounts as owners with the Full Control permission level. An AIP label assigned to research files ensures that they are encrypted and only members of a research group can open them.</span></span>
    
4. <span data-ttu-id="8d36f-120">Migrar archivos de investigación</span><span class="sxs-lookup"><span data-stu-id="8d36f-120">Migrate research files</span></span>
    
    <span data-ttu-id="8d36f-121">Mover el equipo de investigación existentes local archivos y carpetas en el nuevo sitio SharePoint Online de investigación de equipo.</span><span class="sxs-lookup"><span data-stu-id="8d36f-121">Move existing research team on-premises files and folders to the new Research SharePoint Online team site.</span></span>
    
<span data-ttu-id="8d36f-p104">El resultado es que dos sitios de colaboración, cuyo acceso se controla estrechamente por la seguridad y los administradores de SharePoint. Para archivos con la etiqueta altamente confidencial AIP, incluso si se distribuyen fuera del sitio del equipo de investigación, que están encriptados y sólo puede abrirse por un miembro de un equipo de investigación.</span><span class="sxs-lookup"><span data-stu-id="8d36f-p104">The result is two collaboration sites whose access is tightly controlled by security and SharePoint administrators. For files with the Highly Confidential AIP label, even if they are distributed outside the Research team site, they are encrypted and can only be opened by a member of a research team.</span></span>
  
<span data-ttu-id="8d36f-124">Para obtener más información, vea [archivos y sitios de SharePoint Online seguro](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-and-files).</span><span class="sxs-lookup"><span data-stu-id="8d36f-124">For more information, see [Secure SharePoint Online sites and files](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-and-files).</span></span>
  
 <span data-ttu-id="8d36f-125">Para utilizar esta configuración para pruebas y desarrollo, prueba de concepto o demostración, vea [sitios seguro en línea de SharePoint en un entorno de pruebas y desarrollo](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-dev-test).</span><span class="sxs-lookup"><span data-stu-id="8d36f-125">To set this up for demonstration, proof-of-concept, or dev/test, see [Secure SharePoint Online sites in a dev/test environment](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-dev-test).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8d36f-126">Vea también</span><span class="sxs-lookup"><span data-stu-id="8d36f-126">See Also</span></span>

[<span data-ttu-id="8d36f-127">Escenarios empresariales para Contoso Corporation</span><span class="sxs-lookup"><span data-stu-id="8d36f-127">Enterprise scenarios for the Contoso Corporation</span></span>](enterprise-scenarios-for-the-contoso-corporation.md)
  
[<span data-ttu-id="8d36f-128">Contoso en la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="8d36f-128">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="8d36f-129">Recursos de arquitectura de TI de la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="8d36f-129">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="8d36f-130">Stretch Database</span><span class="sxs-lookup"><span data-stu-id="8d36f-130">Stretch Database</span></span>](https://msdn.microsoft.com/library/dn935011.aspx)
  
[<span data-ttu-id="8d36f-131">Mapa de ruta de Enterprise Cloud de Microsoft: Recursos para los responsables de la toma de decisiones de TI</span><span class="sxs-lookup"><span data-stu-id="8d36f-131">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)




