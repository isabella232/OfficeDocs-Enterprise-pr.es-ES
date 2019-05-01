---
title: Sitios de Internet en Microsoft Azure con SharePoint Server 2013
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 0d93ff4a-8fbd-42b8-9227-d817dba0046d
description: 'Resumen: los sitios de Internet que usan SharePoint Server 2013 tienen la ventaja de que se hospedan en Servicios de infraestructura de Azure. En este artículo se ofrecen recursos para diseñar e implementar esta solución.'
ms.openlocfilehash: 26578133709959964e2f8ab1d01b562a526febcb
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487916"
---
# <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a><span data-ttu-id="27d23-104">Sitios de Internet en Microsoft Azure con SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="27d23-104">Internet Sites in Microsoft Azure using SharePoint Server 2013</span></span>

 <span data-ttu-id="27d23-p102">**Resumen:** los sitios de Internet que usan SharePoint Server 2013 tienen la ventaja de que se hospedan en Servicios de infraestructura de Azure. En este artículo se ofrecen recursos para diseñar e implementar esta solución.</span><span class="sxs-lookup"><span data-stu-id="27d23-p102">**Summary:** Internet sites that use SharePoint Server 2013 benefit by being hosted in Azure Infrastructure Services. This article provides resources for designing and implementing this solution.</span></span>
  
## <a name="using-azure-infrastructure-services-for-internet-sites"></a><span data-ttu-id="27d23-107">Usar los Servicios de infraestructura de Azure para sitios de Internet</span><span class="sxs-lookup"><span data-stu-id="27d23-107">Using Azure Infrastructure Services for Internet sites</span></span>

<span data-ttu-id="27d23-p103">Microsoft Azure ofrece una opción atractiva para hospedar sitios de Internet basados en SharePoint Server 2013. Estas son algunas de las ventajas que ofrece:</span><span class="sxs-lookup"><span data-stu-id="27d23-p103">Microsoft Azure provides a compelling option for hosting Internet sites based on SharePoint Server 2013. Advantages include the following:</span></span>
  
- <span data-ttu-id="27d23-110">Centrarse en desarrollar un sitio excelente en lugar de crear la infraestructura.</span><span class="sxs-lookup"><span data-stu-id="27d23-110">Focus on developing a great site instead of building infrastructure.</span></span>
    
- <span data-ttu-id="27d23-111">Flexibilidad para escalar y reducir horizontalmente la solución según la demanda.</span><span class="sxs-lookup"><span data-stu-id="27d23-111">Flexibility to scale your solution based on demand by scaling out and in.</span></span>
    
- <span data-ttu-id="27d23-112">Pagar solo por los recursos que necesita y usa.</span><span class="sxs-lookup"><span data-stu-id="27d23-112">Pay only for the resources that you need and use.</span></span>
    
- <span data-ttu-id="27d23-113">Aprovechar Azure Active Directory para cuentas de clientes.</span><span class="sxs-lookup"><span data-stu-id="27d23-113">Take advantage of Azure Active Directory for customer accounts.</span></span>
    
- <span data-ttu-id="27d23-114">Agregar características que no se ofrecen actualmente en Office 365, como informes detallados y estudios analíticos.</span><span class="sxs-lookup"><span data-stu-id="27d23-114">Add features that are not currently available in Office 365, such as deep reporting and analytics.</span></span>
    
## <a name="resources"></a><span data-ttu-id="27d23-115">Recursos</span><span class="sxs-lookup"><span data-stu-id="27d23-115">Resources</span></span>

<span data-ttu-id="27d23-116">Los artículos e ilustraciones técnicas que detallamos a continuación ofrecen información sobre el procedimiento para diseñar e implementar sitios de Internet en Azure mediante SharePoint Server 2013.</span><span class="sxs-lookup"><span data-stu-id="27d23-116">The following technical illustrations and articles provide information about how to design and implement Internet sites in Azure by using SharePoint Server 2013.</span></span>
  
|<span data-ttu-id="27d23-117">**Recurso**</span><span class="sxs-lookup"><span data-stu-id="27d23-117">**Resource**</span></span>|<span data-ttu-id="27d23-118">**Más información**</span><span class="sxs-lookup"><span data-stu-id="27d23-118">**More information**</span></span>|
|:-----|:-----|
|<span data-ttu-id="27d23-119">Sitios de Internet de **SharePoint Server 2013 en Azure**</span><span class="sxs-lookup"><span data-stu-id="27d23-119">**SharePoint Server 2013 Internet sites in Azure**</span></span> <br/> <span data-ttu-id="27d23-120">[![Imagen de sitios de Internet en Azure usando SharePoint](media/MS-AZ-SPInternetSites.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span><span class="sxs-lookup"><span data-stu-id="27d23-120">[![Image of Internet sites in Azure using SharePoint](media/MS-AZ-SPInternetSites.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span></span> <br/> <span data-ttu-id="27d23-121">[](https://go.microsoft.com/fwlink/p/?LinkId=392552)\| PDF [           ](https://go.microsoft.com/fwlink/p/?LinkId=392551)de [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)  </span><span class="sxs-lookup"><span data-stu-id="27d23-121">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)  \| [          ](https://go.microsoft.com/fwlink/p/?LinkId=392551)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)</span></span> <br/> |<span data-ttu-id="27d23-122">En este modelo de arquitectura se describen las principales actividades de diseño y las opciones de arquitectura recomendadas para sitios de Internet en Azure.</span><span class="sxs-lookup"><span data-stu-id="27d23-122">This architecture model outlines key design activities and recommended architecture choices for Internet sites in Azure.</span></span>  <br/> |
|<span data-ttu-id="27d23-123">**Ejemplo de diseño: sitios de Internet en Azure para SharePoint Server 2013**</span><span class="sxs-lookup"><span data-stu-id="27d23-123">**Design sample: Internet Sites in Azure for SharePoint Server 2013**</span></span> <br/> <span data-ttu-id="27d23-124">[![Imagen de la muestra de diseño: sitios de Internet en Microsoft Azure para SharePoint 2013](media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span><span class="sxs-lookup"><span data-stu-id="27d23-124">[![Image of the Design sample: Internet sites in Microsoft Azure for SharePoint 2013](media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span></span> <br/> <span data-ttu-id="27d23-125">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)</span><span class="sxs-lookup"><span data-stu-id="27d23-125">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)</span></span> <br/> |<span data-ttu-id="27d23-126">Use este ejemplo de diseño como punto de partida para su propia arquitectura.</span><span class="sxs-lookup"><span data-stu-id="27d23-126">Use this design sample as a starting point for your own architecture.</span></span>  <br/> |
|<span data-ttu-id="27d23-127">**[Arquitecturas de Microsoft Azure para SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)**</span><span class="sxs-lookup"><span data-stu-id="27d23-127">**[Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)**</span></span> <br/> |<span data-ttu-id="27d23-128">En este artículo se describe cómo diseñar arquitecturas de Azure para hospedar soluciones de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="27d23-128">This article describes how to design Azure architectures to host SharePoint solutions.</span></span>  <br/> |

   
<span data-ttu-id="27d23-129">**Participar en el debate**</span><span class="sxs-lookup"><span data-stu-id="27d23-129">**Join the discussion**</span></span>

|<span data-ttu-id="27d23-130">**Póngase en contacto con nosotros**</span><span class="sxs-lookup"><span data-stu-id="27d23-130">**Contact us**</span></span>|<span data-ttu-id="27d23-131">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="27d23-131">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="27d23-132">**¿Qué soluciones necesita?**</span><span class="sxs-lookup"><span data-stu-id="27d23-132">**What cloud adoption content do you need?**</span></span> <br/> |<span data-ttu-id="27d23-p104">Estamos creando contenido para soluciones que abarcan varios productos y servicios de Microsoft. Díganos qué piensa sobre nuestras soluciones entre servidores o solicite soluciones específicas por correo electrónico a [MODAcontent@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).</span><span class="sxs-lookup"><span data-stu-id="27d23-p104">We are creating content for cloud adoption that spans multiple Microsoft cloud platforms and services. Let us know what you think about our cloud adoption content, or ask for specific content by sending email to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).  </span></span><br/> |
|<span data-ttu-id="27d23-135">**Participe en la discusión sobre soluciones**</span><span class="sxs-lookup"><span data-stu-id="27d23-135">**Join the cloud adoption discussion**</span></span> <br/> |<span data-ttu-id="27d23-p105">Si es un apasionado de las soluciones basadas en la nube, puede unirse a Cloud Adoption Advisory Board (CAAB) para conectarse a una interesante comunidad de mayor tamaño formada por desarrolladores de contenido de Microsoft, profesionales del sector y clientes de todo el mundo. Para unirse, agregue a su usuario como miembro del [espacio CAAB (Cloud Adoption Advisory Board)](https://aka.ms/caab) de Microsoft Tech Community y envíenos un correo electrónico a [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Cualquiera puede leer contenido relacionado con la comunidad en el [blog de CAAB](https://blogs.technet.com/b/solutions_advisory_board/). Pero los miembros de CAAB reciben invitaciones a seminarios web privados donde se describen nuevos recursos y soluciones de adopción de la nube.  </span><span class="sxs-lookup"><span data-stu-id="27d23-p105">If you are passionate about cloud-based solutions, consider joining the Cloud Adoption Advisory Board (CAAB) to connect with a larger, vibrant community of Microsoft content developers, industry professionals, and customers from around the globe. To join, add yourself as a member of the [CAAB (Cloud Adoption Advisory Board) space](https://aka.ms/caab) of the Microsoft Tech Community and send us a quick email at[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Anyone can read community-related content on the [CAAB blog](https://blogs.technet.com/b/solutions_advisory_board/). However, CAAB members get invitations to private webinars that describe new cloud adoption resources and solutions.  </span></span><br/> |
|<span data-ttu-id="27d23-140">**Obtenga los archivos de arte que ve aquí**</span><span class="sxs-lookup"><span data-stu-id="27d23-140">**Get the art you see here**</span></span> <br/> |<span data-ttu-id="27d23-p106">Si quiere recibir una copia editable de las ilustraciones que se muestran en este artículo, estaremos encantados de enviárselas. Envíe su solicitud por correo electrónico, incluida la dirección URL y el título de la ilustración, a [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  </span><span class="sxs-lookup"><span data-stu-id="27d23-p106">If you want an editable copy of the art you see in this article, we'll be glad to send it to you. Email your request, including the URL and title of the art, to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  </span></span><br/> |
   
## <a name="see-also"></a><span data-ttu-id="27d23-143">Vea también</span><span class="sxs-lookup"><span data-stu-id="27d23-143">See Also</span></span>

[<span data-ttu-id="27d23-144">Adopción de la nube y soluciones híbridas</span><span class="sxs-lookup"><span data-stu-id="27d23-144">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)



