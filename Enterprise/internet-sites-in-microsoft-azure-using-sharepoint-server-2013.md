---
title: Sitios de Internet en Microsoft Azure con SharePoint Server 2013
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Architecture
ms.assetid: 0d93ff4a-8fbd-42b8-9227-d817dba0046d
description: 'Resumen: los sitios de Internet que usan SharePoint Server 2013 tienen la ventaja de que se hospedan en Servicios de infraestructura de Azure. En este artículo se ofrecen recursos para diseñar e implementar esta solución.'
ms.openlocfilehash: f32b58c7c163bb9afa409b8a4a2a53c5445965dd
ms.sourcegitcommit: a578baeb0d8b85941c13afa268447d2592f89fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2020
ms.locfileid: "43793753"
---
# <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a><span data-ttu-id="133f8-104">Sitios de Internet en Microsoft Azure con SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="133f8-104">Internet Sites in Microsoft Azure using SharePoint Server 2013</span></span>

 <span data-ttu-id="133f8-p102">**Resumen:** los sitios de Internet que usan SharePoint Server 2013 tienen la ventaja de que se hospedan en Servicios de infraestructura de Azure. En este artículo se ofrecen recursos para diseñar e implementar esta solución.</span><span class="sxs-lookup"><span data-stu-id="133f8-p102">**Summary:** Internet sites that use SharePoint Server 2013 benefit by being hosted in Azure Infrastructure Services. This article provides resources for designing and implementing this solution.</span></span>
  
## <a name="using-azure-infrastructure-services-for-internet-sites"></a><span data-ttu-id="133f8-107">Usar los Servicios de infraestructura de Azure para sitios de Internet</span><span class="sxs-lookup"><span data-stu-id="133f8-107">Using Azure Infrastructure Services for Internet sites</span></span>

<span data-ttu-id="133f8-p103">Microsoft Azure ofrece una opción atractiva para hospedar sitios de Internet basados en SharePoint Server 2013. Estas son algunas de las ventajas que ofrece:</span><span class="sxs-lookup"><span data-stu-id="133f8-p103">Microsoft Azure provides a compelling option for hosting Internet sites based on SharePoint Server 2013. Advantages include the following:</span></span>
  
- <span data-ttu-id="133f8-110">Centrarse en desarrollar un sitio excelente en lugar de crear la infraestructura.</span><span class="sxs-lookup"><span data-stu-id="133f8-110">Focus on developing a great site instead of building infrastructure.</span></span>
    
- <span data-ttu-id="133f8-111">Flexibilidad para escalar y reducir horizontalmente la solución según la demanda.</span><span class="sxs-lookup"><span data-stu-id="133f8-111">Flexibility to scale your solution based on demand by scaling out and in.</span></span>
    
- <span data-ttu-id="133f8-112">Pagar solo por los recursos que necesita y usa.</span><span class="sxs-lookup"><span data-stu-id="133f8-112">Pay only for the resources that you need and use.</span></span>
    
- <span data-ttu-id="133f8-113">Aprovechar Azure Active Directory para cuentas de clientes.</span><span class="sxs-lookup"><span data-stu-id="133f8-113">Take advantage of Azure Active Directory for customer accounts.</span></span>
    
- <span data-ttu-id="133f8-114">Agregar características que no se ofrecen actualmente en Office 365, como informes detallados y estudios analíticos.</span><span class="sxs-lookup"><span data-stu-id="133f8-114">Add features that are not currently available in Office 365, such as deep reporting and analytics.</span></span>
    
## <a name="resources"></a><span data-ttu-id="133f8-115">Recursos</span><span class="sxs-lookup"><span data-stu-id="133f8-115">Resources</span></span>

<span data-ttu-id="133f8-116">Los artículos e ilustraciones técnicas que detallamos a continuación ofrecen información sobre el procedimiento para diseñar e implementar sitios de Internet en Azure mediante SharePoint Server 2013.</span><span class="sxs-lookup"><span data-stu-id="133f8-116">The following technical illustrations and articles provide information about how to design and implement Internet sites in Azure by using SharePoint Server 2013.</span></span>
  
|<span data-ttu-id="133f8-117">**Recurso**</span><span class="sxs-lookup"><span data-stu-id="133f8-117">**Resource**</span></span>|<span data-ttu-id="133f8-118">**Más información**</span><span class="sxs-lookup"><span data-stu-id="133f8-118">**More information**</span></span>|
|:-----|:-----|
|<span data-ttu-id="133f8-119">Sitios de Internet de **SharePoint Server 2013 en Azure**</span><span class="sxs-lookup"><span data-stu-id="133f8-119">**SharePoint Server 2013 Internet sites in Azure**</span></span> <br/> <span data-ttu-id="133f8-120">[![Imagen de sitios de Internet en Azure usando SharePoint](media/MS-AZ-SPInternetSites.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span><span class="sxs-lookup"><span data-stu-id="133f8-120">[![Image of Internet sites in Azure using SharePoint](media/MS-AZ-SPInternetSites.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span></span> <br/> <span data-ttu-id="133f8-121">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)\| PDF [           ](https://go.microsoft.com/fwlink/p/?LinkId=392551)de [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)  </span><span class="sxs-lookup"><span data-stu-id="133f8-121">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)  \| [          ](https://go.microsoft.com/fwlink/p/?LinkId=392551)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)</span></span> <br/> |<span data-ttu-id="133f8-122">En este modelo de arquitectura se describen las principales actividades de diseño y las opciones de arquitectura recomendadas para sitios de Internet en Azure.</span><span class="sxs-lookup"><span data-stu-id="133f8-122">This architecture model outlines key design activities and recommended architecture choices for Internet sites in Azure.</span></span>  <br/> |
|<span data-ttu-id="133f8-123">**Ejemplo de diseño: sitios de Internet en Azure para SharePoint Server 2013**</span><span class="sxs-lookup"><span data-stu-id="133f8-123">**Design sample: Internet Sites in Azure for SharePoint Server 2013**</span></span> <br/> <span data-ttu-id="133f8-124">[![Imagen de la muestra de diseño: sitios de Internet en Microsoft Azure para SharePoint 2013](media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span><span class="sxs-lookup"><span data-stu-id="133f8-124">[![Image of the Design sample: Internet sites in Microsoft Azure for SharePoint 2013](media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span></span> <br/> <span data-ttu-id="133f8-125">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)</span><span class="sxs-lookup"><span data-stu-id="133f8-125">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)</span></span> <br/> |<span data-ttu-id="133f8-126">Use este ejemplo de diseño como punto de partida para su propia arquitectura.</span><span class="sxs-lookup"><span data-stu-id="133f8-126">Use this design sample as a starting point for your own architecture.</span></span>  <br/> |
|<span data-ttu-id="133f8-127">**[Arquitecturas de Microsoft Azure para SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)**</span><span class="sxs-lookup"><span data-stu-id="133f8-127">**[Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)**</span></span> <br/> |<span data-ttu-id="133f8-128">En este artículo se describe cómo diseñar arquitecturas de Azure para hospedar soluciones de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="133f8-128">This article describes how to design Azure architectures to host SharePoint solutions.</span></span>  <br/> |

## <a name="see-also"></a><span data-ttu-id="133f8-129">Vea también</span><span class="sxs-lookup"><span data-stu-id="133f8-129">See Also</span></span>

[<span data-ttu-id="133f8-130">Adopción de la nube y soluciones híbridas</span><span class="sxs-lookup"><span data-stu-id="133f8-130">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.yml)



