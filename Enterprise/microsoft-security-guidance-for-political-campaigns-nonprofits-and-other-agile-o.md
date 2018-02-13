---
title: "Guía de seguridad de Microsoft para campañas políticas, las ONG y otras organizaciones de Agile"
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.collection: Ent_O365, Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Normal
ms.custom: Strat_O365_Enterprise
ms.assetid: 10d1004b-42b6-4e2b-aaa2-18ddd9118f64
description: "Resumen: Guía de planificación e implementación para el movimiento rápido las organizaciones que tengan un perfil de amenaza elevado."
ms.openlocfilehash: 30a45cfa521c73689afa7481cbe7ba9637b97617
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/13/2018
---
# <a name="microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-organizations"></a><span data-ttu-id="981c2-103">Guía de seguridad de Microsoft para campañas políticas, las ONG y otras organizaciones de Agile</span><span class="sxs-lookup"><span data-stu-id="981c2-103">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>

 <span data-ttu-id="981c2-104">**Resumen:** Guía de planificación e implementación para el movimiento rápido las organizaciones que tengan un perfil de amenaza elevado.</span><span class="sxs-lookup"><span data-stu-id="981c2-104">**Summary:** Planning and implementation guidance for fast-moving organizations that have an increased threat profile.</span></span>
  
<span data-ttu-id="981c2-p101">Si su organización es ágil, tiene un pequeño equipo de TI y tu perfil de amenaza es mayor que el promedio, esta guía está diseñada para usted. Esta solución muestra cómo crear rápidamente un entorno de servicios de nube esenciales que incluyen controles seguros desde el principio. Esta guía incluye recomendaciones de directrices de seguridad para la protección de datos, las identidades, correo electrónico y acceso desde dispositivos móviles.</span><span class="sxs-lookup"><span data-stu-id="981c2-p101">If your organization is agile, you have a small IT team, and your threat profile is higher than average, this guidance is designed for you. This solution demonstrates how to quickly build an environment with essential cloud services that include secure controls from the start. This guidance includes prescriptive security recommendations for protecting data, identities, email, and access from mobile devices.</span></span>
  
## <a name="security-solution-guidance"></a><span data-ttu-id="981c2-108">Guía de soluciones de seguridad</span><span class="sxs-lookup"><span data-stu-id="981c2-108">Security solution guidance</span></span>

<span data-ttu-id="981c2-p102">Esta guía describe cómo implementar un entorno de nube segura. La Guía de la solución puede utilizarse por cualquier organización. Incluye ayuda adicional para organizaciones ágiles con las cuentas de invitado y el acceso BYOD. Puede utilizar esta guía como punto de partida para diseñar su propio entorno. Le agradecemos sus comentarios a [CloudAdopt@microsoft.com](mailto:CloudAdopt@microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="981c2-p102">This guidance describes how to implement a secure cloud environment. The solution guidance can be used by any organization. It includes extra help for agile organizations with BYOD access and guest accounts. You can use this guidance as a starting-point for designing your own environment. We welcome your feedback at [CloudAdopt@microsoft.com](mailto:CloudAdopt@microsoft.com).</span></span> 
  
|||
|:-----|:-----|
|<span data-ttu-id="981c2-114">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="981c2-114">**Item**</span></span> <br/> |<span data-ttu-id="981c2-115">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="981c2-115">**Description**</span></span> <br/> |
|<span data-ttu-id="981c2-116">**Guía de seguridad de Microsoft para campañas políticas**</span><span class="sxs-lookup"><span data-stu-id="981c2-116">**Microsoft Security Guidance for Political Campaigns**</span></span> <br/> <span data-ttu-id="981c2-117">[![Clavo de póster mini conjunto del pulgar.](images/d370ce28-ca40-4930-9a2c-907312aa06c8.png)          ](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)</span><span class="sxs-lookup"><span data-stu-id="981c2-117">[![Thumb nail for mini poster set.](images/d370ce28-ca40-4930-9a2c-907312aa06c8.png)          ](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)</span></span> <br/> <span data-ttu-id="981c2-118">[PDF](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf) \| [Visio](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.vsdx)  </span><span class="sxs-lookup"><span data-stu-id="981c2-118">[PDF](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)  \| [Visio](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.vsdx)</span></span> <br/> |<span data-ttu-id="981c2-p103">Esta guía utiliza como ejemplo una organización de campaña política. Utilice esta guía como punto de partida para cualquier entorno.</span><span class="sxs-lookup"><span data-stu-id="981c2-p103">This guidance uses a political campaign organization as an example. Use this guidance as a starting point for any environment.</span></span>  <br/> |
|<span data-ttu-id="981c2-121">**Guía de seguridad de Microsoft para organizaciones no lucrativas**</span><span class="sxs-lookup"><span data-stu-id="981c2-121">**Microsoft Security Guidance for Nonprofits**</span></span> <br/> <span data-ttu-id="981c2-122">[![Imagen de miniaturas para archivo descargable](images/e4784889-1c69-4067-9a8f-31d31d1eceea.png)          ](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)</span><span class="sxs-lookup"><span data-stu-id="981c2-122">[![Thumnail image for downloadable file](images/e4784889-1c69-4067-9a8f-31d31d1eceea.png)          ](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)</span></span> <br/> <span data-ttu-id="981c2-123">[PDF](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf) \| [Visio](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.vsdx)  </span><span class="sxs-lookup"><span data-stu-id="981c2-123">[PDF](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)  \| [Visio](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.vsdx)</span></span> <br/> |<span data-ttu-id="981c2-p104">Esta guía es ligeramente revisada para organizaciones sin ánimo de lucro. Por ejemplo, hace referencia a planes sin ánimo de lucro de Office 365. La orientación técnica es la misma que la Guía de solución de campaña política.</span><span class="sxs-lookup"><span data-stu-id="981c2-p104">This guide is slightly revised for nonprofit organizations. For example, it references Office 365 Nonprofit plans. The technical guidance is the same as the political campaign solution guide.</span></span>  <br/> |
   
## <a name="test-lab-guides"></a><span data-ttu-id="981c2-127">Guía de entornos de pruebas</span><span class="sxs-lookup"><span data-stu-id="981c2-127">Test Lab Guides</span></span>

<span data-ttu-id="981c2-128">Para crear un entorno de desarrollo y prueba de esta solución, utilice las siguientes guías de laboratorio de prueba:</span><span class="sxs-lookup"><span data-stu-id="981c2-128">To create a dev/test environment for this solution, use the following test lab guides:</span></span> 
  
- [<span data-ttu-id="981c2-129">Configurar grupos y usuarios de un entorno de pruebas y desarrollo de campaña política</span><span class="sxs-lookup"><span data-stu-id="981c2-129">Configure groups and users for a political campaign dev/test environment</span></span>](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)
    
     <span data-ttu-id="981c2-130">Crear suscripciones de prueba de Office 365 y EMS y, a continuación, crear grupos y usuarios para una campaña político representativo.</span><span class="sxs-lookup"><span data-stu-id="981c2-130">Create trial subscriptions for Office 365 and EMS and then create groups and users for a representative political campaign.</span></span>
    
- [<span data-ttu-id="981c2-131">Crear sitios de equipo en un entorno de pruebas y desarrollo de campaña política</span><span class="sxs-lookup"><span data-stu-id="981c2-131">Create team sites in a political campaign dev/test environment</span></span>](create-team-sites-in-a-political-campaign-dev-test-environment.md)
    
    <span data-ttu-id="981c2-132">Cree cuatro sitios de equipo de SharePoint Online con niveles internos, privados, sensible y altamente confidencial de seguridad.</span><span class="sxs-lookup"><span data-stu-id="981c2-132">Create four SharePoint Online team sites with Internal, Private, Sensitive, and Highly Confidential levels of security.</span></span>
    
<span data-ttu-id="981c2-133">Para las características de seguridad adicionales para la demostración o prueba del concepto, consulte [Guías de laboratorio de prueba de Office 365](http://aka.ms/o365tlgs).</span><span class="sxs-lookup"><span data-stu-id="981c2-133">For additional security features for demonstration or proof of concept, see [Office 365 Test Lab Guides](http://aka.ms/o365tlgs).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="981c2-134">Consulte también</span><span class="sxs-lookup"><span data-stu-id="981c2-134">See Also</span></span>

[<span data-ttu-id="981c2-135">Soluciones de seguridad</span><span class="sxs-lookup"><span data-stu-id="981c2-135">Security solutions</span></span>](security-solutions.md)
  
[<span data-ttu-id="981c2-136">Guías de entorno de pruebas de adopción de la nube (TLG)</span><span class="sxs-lookup"><span data-stu-id="981c2-136">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="981c2-137">Recursos de arquitectura de TI de la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="981c2-137">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)



