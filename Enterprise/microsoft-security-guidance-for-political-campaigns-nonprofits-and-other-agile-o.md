---
title: "Guía de seguridad de Microsoft para campañas políticas, las ONG y otras organizaciones de Agile"
ms.author: bcarter
author: bcarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
ms.assetid: 10d1004b-42b6-4e2b-aaa2-18ddd9118f64
description: "Resumen: Guía de planificación e implementación para el movimiento rápido las organizaciones que tengan un perfil de amenaza elevado."
ms.openlocfilehash: 632cb63877e159f18707dbf68eb7733082319654
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2017
---
# <a name="microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-organizations"></a><span data-ttu-id="e2031-103">Guía de seguridad de Microsoft para campañas políticas, las ONG y otras organizaciones de Agile</span><span class="sxs-lookup"><span data-stu-id="e2031-103">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>

 <span data-ttu-id="e2031-104">**Resumen:** Guía de planificación e implementación para el movimiento rápido las organizaciones que tengan un perfil de amenaza elevado.</span><span class="sxs-lookup"><span data-stu-id="e2031-104">**Summary:** Planning and implementation guidance for fast-moving organizations that have an increased threat profile.</span></span>
  
<span data-ttu-id="e2031-p101">Si su organización es ágil, tiene un pequeño equipo de TI y tu perfil de amenaza es mayor que el promedio, esta guía está diseñada para usted. Esta solución muestra cómo crear rápidamente un entorno de servicios de nube esenciales que incluyen controles seguros desde el principio. Esta guía incluye recomendaciones de directrices de seguridad para la protección de datos, las identidades, correo electrónico y acceso desde dispositivos móviles.</span><span class="sxs-lookup"><span data-stu-id="e2031-p101">If your organization is agile, you have a small IT team, and your threat profile is higher than average, this guidance is designed for you. This solution demonstrates how to quickly build an environment with essential cloud services that include secure controls from the start. This guidance includes prescriptive security recommendations for protecting data, identities, email, and access from mobile devices.</span></span>
  
## <a name="security-solution-guidance"></a><span data-ttu-id="e2031-108">Guía de soluciones de seguridad</span><span class="sxs-lookup"><span data-stu-id="e2031-108">Security solution guidance</span></span>

<span data-ttu-id="e2031-p102">Esta guía describe cómo implementar un entorno de nube segura. La Guía de la solución puede utilizarse por cualquier organización. Incluye ayuda adicional para organizaciones ágiles con las cuentas de invitado y el acceso BYOD. Puede utilizar esta guía como punto de partida para diseñar su propio entorno. Le agradecemos sus comentarios a [CloudAdopt@microsoft.com](mailto:CloudAdopt@microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="e2031-p102">This guidance describes how to implement a secure cloud environment. The solution guidance can be used by any organization. It includes extra help for agile organizations with BYOD access and guest accounts. You can use this guidance as a starting-point for designing your own environment. We welcome your feedback at [CloudAdopt@microsoft.com](mailto:CloudAdopt@microsoft.com).</span></span> 
  
|||
|:-----|:-----|
|<span data-ttu-id="e2031-114">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="e2031-114">**Item**</span></span> <br/> |<span data-ttu-id="e2031-115">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="e2031-115">**Description**</span></span> <br/> |
|<span data-ttu-id="e2031-116">**Guía de seguridad de Microsoft para campañas políticas**</span><span class="sxs-lookup"><span data-stu-id="e2031-116">**Microsoft Security Guidance for Political Campaigns**</span></span> <br/> <span data-ttu-id="e2031-117">[![Clavo de póster mini conjunto del pulgar.](images/d370ce28-ca40-4930-9a2c-907312aa06c8.png)          ](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)</span><span class="sxs-lookup"><span data-stu-id="e2031-117">[![Thumb nail for mini poster set.](images/d370ce28-ca40-4930-9a2c-907312aa06c8.png)          ](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)</span></span> <br/> <span data-ttu-id="e2031-118">[PDF](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)  \\</span><span class="sxs-lookup"><span data-stu-id="e2031-118">[PDF](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)  \\</span></span>| [<span data-ttu-id="e2031-119">Visio</span><span class="sxs-lookup"><span data-stu-id="e2031-119">Visio</span></span>](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.vsdx) <br/> |<span data-ttu-id="e2031-p103">Esta guía utiliza como ejemplo una organización de campaña política. Utilice esta guía como punto de partida para cualquier entorno.</span><span class="sxs-lookup"><span data-stu-id="e2031-p103">This guidance uses a political campaign organization as an example. Use this guidance as a starting point for any environment.</span></span>  <br/> |
|<span data-ttu-id="e2031-122">**Guía de seguridad de Microsoft para organizaciones no lucrativas**</span><span class="sxs-lookup"><span data-stu-id="e2031-122">**Microsoft Security Guidance for Nonprofits**</span></span> <br/> <span data-ttu-id="e2031-123">[![Imagen de miniaturas para archivo descargable](images/e4784889-1c69-4067-9a8f-31d31d1eceea.png)          ](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)</span><span class="sxs-lookup"><span data-stu-id="e2031-123">[![Thumnail image for downloadable file](images/e4784889-1c69-4067-9a8f-31d31d1eceea.png)          ](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)</span></span> <br/> <span data-ttu-id="e2031-124">[PDF](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)  \\</span><span class="sxs-lookup"><span data-stu-id="e2031-124">[PDF](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)  \\</span></span>| [<span data-ttu-id="e2031-125">Visio</span><span class="sxs-lookup"><span data-stu-id="e2031-125">Visio</span></span>](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.vsdx) <br/> |<span data-ttu-id="e2031-p104">Esta guía es ligeramente revisada para organizaciones sin ánimo de lucro. Por ejemplo, hace referencia a planes sin ánimo de lucro de Office 365. La orientación técnica es la misma que la Guía de solución de campaña política.</span><span class="sxs-lookup"><span data-stu-id="e2031-p104">This guide is slightly revised for nonprofit organizations. For example, it references Office 365 Nonprofit plans. The technical guidance is the same as the political campaign solution guide.</span></span>  <br/> |
   
## <a name="test-lab-guides"></a><span data-ttu-id="e2031-129">Guía de entornos de pruebas</span><span class="sxs-lookup"><span data-stu-id="e2031-129">Test Lab Guides</span></span>

<span data-ttu-id="e2031-130">Para crear un entorno de desarrollo y prueba de esta solución, utilice las siguientes guías de laboratorio de prueba:</span><span class="sxs-lookup"><span data-stu-id="e2031-130">To create a dev/test environment for this solution, use the following test lab guides:</span></span> 
  
- [<span data-ttu-id="e2031-131">Configurar grupos y usuarios de un entorno de pruebas y desarrollo de campaña política</span><span class="sxs-lookup"><span data-stu-id="e2031-131">Configure groups and users for a political campaign dev/test environment</span></span>](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)
    
     <span data-ttu-id="e2031-132">Crear suscripciones de prueba de Office 365 y EMS y, a continuación, crear grupos y usuarios para una campaña político representativo.</span><span class="sxs-lookup"><span data-stu-id="e2031-132">Create trial subscriptions for Office 365 and EMS and then create groups and users for a representative political campaign.</span></span>
    
- [<span data-ttu-id="e2031-133">Crear sitios de equipo en un entorno de pruebas y desarrollo de campaña política</span><span class="sxs-lookup"><span data-stu-id="e2031-133">Create team sites in a political campaign dev/test environment</span></span>](create-team-sites-in-a-political-campaign-dev-test-environment.md)
    
    <span data-ttu-id="e2031-134">Cree cuatro sitios de equipo de SharePoint Online con niveles internos, privados, sensible y altamente confidencial de seguridad.</span><span class="sxs-lookup"><span data-stu-id="e2031-134">Create four SharePoint Online team sites with Internal, Private, Sensitive, and Highly Confidential levels of security.</span></span>
    
<span data-ttu-id="e2031-135">Para las características de seguridad adicionales para la demostración o prueba del concepto, consulte [Guías de laboratorio de prueba de Office 365](http://aka.ms/o365tlgs).</span><span class="sxs-lookup"><span data-stu-id="e2031-135">For additional security features for demonstration or proof of concept, see [Office 365 Test Lab Guides](http://aka.ms/o365tlgs).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e2031-136">See Also</span><span class="sxs-lookup"><span data-stu-id="e2031-136">See Also</span></span>

[<span data-ttu-id="e2031-137">Soluciones de seguridad</span><span class="sxs-lookup"><span data-stu-id="e2031-137">Security solutions</span></span>](security-solutions.md)
  
[<span data-ttu-id="e2031-138">Guías del laboratorio de pruebas de adopción de la nube (TLG)</span><span class="sxs-lookup"><span data-stu-id="e2031-138">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="e2031-139">Recursos de arquitectura de TI de la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="e2031-139">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)



