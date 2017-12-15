---
title: Infraestructura y necesidades de TI de Contoso
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 5d6a58b8-bec3-4629-9737-8733c7b7ec92
description: "Resumen: Comprender la estructura básica de la infraestructura de TI local de Contoso y cómo sus necesidades de negocio pueden cumplirse mediante ofertas de nube de Microsoft."
ms.openlocfilehash: 98ead7ffa3164c3cd57ec50def836b690881ba63
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2017
---
# <a name="contosos-it-infrastructure-and-needs"></a><span data-ttu-id="fb496-103">Infraestructura y necesidades de TI de Contoso</span><span class="sxs-lookup"><span data-stu-id="fb496-103">Contoso's IT infrastructure and needs</span></span>

 <span data-ttu-id="fb496-104">**Resumen:** Comprender la estructura básica de la infraestructura de TI local de Contoso y cómo sus necesidades de negocio pueden cumplirse mediante ofertas de nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="fb496-104">**Summary:** Understand the basic structure of Contoso's on-premises IT infrastructure and how its business needs can be met by Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="fb496-105">Contoso está en proceso de transición de una infraestructura de TI centralizada local a una infraestructura de nube inclusiva que incorpora las cargas de trabajo de productividad del personal, las aplicaciones y los escenarios híbridos basados en la nube.</span><span class="sxs-lookup"><span data-stu-id="fb496-105">Contoso is in the process of transitioning from an on-premises, centralized IT infrastructure to a cloud-inclusive one that incorporates cloud-based personal productivity workloads, applications, and hybrid scenarios.</span></span>
  
## <a name="contosos-existing-it-infrastructure"></a><span data-ttu-id="fb496-106">Infraestructura de TI existente de Contoso</span><span class="sxs-lookup"><span data-stu-id="fb496-106">Contoso's existing IT infrastructure</span></span>

<span data-ttu-id="fb496-107">Contoso usa una infraestructura de TI local mayoritariamente centralizada, con centros de datos de aplicaciones en la sede de París.</span><span class="sxs-lookup"><span data-stu-id="fb496-107">Contoso uses a mostly centralized on-premises IT infrastructure, with application datacenters in the Paris headquarters.</span></span>
  
<span data-ttu-id="fb496-108">**Figura 1: Infraestructura de TI existente de Contoso**</span><span class="sxs-lookup"><span data-stu-id="fb496-108">**Figure 1: Contoso's existing IT infrastructure**</span></span>

![Infraestructura de TI existente de Contoso](images/Contoso_Poster/Existing_IT.png)
  
<span data-ttu-id="fb496-110">La figura 1 muestra una oficina central con centros de datos de aplicaciones, una red perimetral e Internet.</span><span class="sxs-lookup"><span data-stu-id="fb496-110">Figure 1 shows a headquarters office with application datacenters, a DMZ, and the Internet.</span></span>
  
<span data-ttu-id="fb496-111">En la red perimetral de Contoso, los distintos conjuntos de servidores proporcionan lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="fb496-111">In Contoso's DMZ, different sets of servers provide:</span></span>
  
- <span data-ttu-id="fb496-112">Acceso remoto al proxy web y a la intranet de Contoso para los trabajadores de la sede de París.</span><span class="sxs-lookup"><span data-stu-id="fb496-112">Remote access to the Contoso intranet and web proxying for workers in the Paris headquarters.</span></span>
    
- <span data-ttu-id="fb496-113">Hospedaje del sitio web público de Contoso, desde el cual los clientes pueden solicitar productos, piezas o suministros.</span><span class="sxs-lookup"><span data-stu-id="fb496-113">Hosting for the Contoso public web site, from which customers can order products, parts, or supplies.</span></span>
    
- <span data-ttu-id="fb496-114">Hospedaje de la extranet de partners de Contoso para la colaboración y comunicación de los partners.</span><span class="sxs-lookup"><span data-stu-id="fb496-114">Hosting for the Contoso partner extranet for partner communication and collaboration.</span></span>
    
## <a name="contosos-business-needs"></a><span data-ttu-id="fb496-115">Necesidades de negocio de Contoso</span><span class="sxs-lookup"><span data-stu-id="fb496-115">Contoso's business needs</span></span>

<span data-ttu-id="fb496-116">Estas son las necesidades de negocio de Contoso en orden de prioridad:</span><span class="sxs-lookup"><span data-stu-id="fb496-116">Here are Contoso's business needs in priority order:</span></span>
  
1. <span data-ttu-id="fb496-117">Cumplir los requisitos normativos regionales</span><span class="sxs-lookup"><span data-stu-id="fb496-117">Adhere to regional regulatory requirements</span></span>
    
    <span data-ttu-id="fb496-118">Para evitar multas y mantener buenas relaciones con los gobiernos locales, Contoso debe garantizar el cumplimiento de las normas de almacenamiento y cifrado de datos.</span><span class="sxs-lookup"><span data-stu-id="fb496-118">To prevent fines and maintain good relations with local governments, Contoso must ensure compliance with data storage and encryption regulations.</span></span>
    
2. <span data-ttu-id="fb496-119">Mejorar la administración de proveedores y partners</span><span class="sxs-lookup"><span data-stu-id="fb496-119">Improve vendor and partner management</span></span>
    
    <span data-ttu-id="fb496-p101">La extranet de partners está quedando anticuada y es cara de mantener. Contoso quiere reemplazarla por una solución basada en la nube que use la autenticación federada.</span><span class="sxs-lookup"><span data-stu-id="fb496-p101">The partner extranet is aging and expensive to maintain. Contoso wants to replace it with a cloud-based solution that uses federated authentication.</span></span>
    
3. <span data-ttu-id="fb496-122">Mejorar la productividad de los empleados móviles, la administración de dispositivos y el acceso</span><span class="sxs-lookup"><span data-stu-id="fb496-122">Improve mobile workforce productivity, device management, and access</span></span>
    
    <span data-ttu-id="fb496-123">El personal exclusivamente móvil de Contoso se está expandiendo y se requiere la administración de dispositivos para garantizar la protección de la propiedad intelectual y un acceso más eficiente a los recursos.</span><span class="sxs-lookup"><span data-stu-id="fb496-123">Contoso's mobile-only workforce is expanding and needs device management to ensure intellectual property protection and more efficient access to resources.</span></span>
    
4. <span data-ttu-id="fb496-124">Reducir la infraestructura de acceso remoto</span><span class="sxs-lookup"><span data-stu-id="fb496-124">Reduce remote access infrastructure</span></span>
    
    <span data-ttu-id="fb496-125">Al mover a la nube recursos a los que los trabajadores remotos tienen acceso con frecuencia, Contoso ahorrará dinero gracias a la reducción de los costos de mantenimiento y soporte técnico de su solución de acceso remoto.</span><span class="sxs-lookup"><span data-stu-id="fb496-125">By moving resources commonly accessed by remote workers to the cloud, Contoso will save money by reducing maintenance and support costs for their remote access solution.</span></span>
    
5. <span data-ttu-id="fb496-126">Reducir verticalmente los centros de datos locales</span><span class="sxs-lookup"><span data-stu-id="fb496-126">Scale down on-premises datacenters</span></span>
    
    <span data-ttu-id="fb496-127">Los centros de datos de Contoso contienen cientos de servidores, algunos de los cuales ejecutan funciones de archivo o heredadas que desvían la atención del personal de TI del mantenimiento de unas cargas de trabajo de alto valor empresarial.</span><span class="sxs-lookup"><span data-stu-id="fb496-127">The Contoso datacenters contain hundreds of servers, some of which are running legacy or archival functions that distract IT staff from maintaining high business value workloads.</span></span>
    
6. <span data-ttu-id="fb496-128">Escalar verticalmente los recursos informáticos y de almacenamiento para el procesamiento de fin de trimestre</span><span class="sxs-lookup"><span data-stu-id="fb496-128">Scale-up computing and storage resources for end-of-quarter processing</span></span>
    
    <span data-ttu-id="fb496-129">El procesamiento de la contabilidad financiera de fin de trimestre y la proyección, junto con la administración del inventario, requiere aumentos a corto plazo en servidores y almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="fb496-129">End-of-quarter financial accounting and projection processing along with inventory management requires short-term increases in servers and storage.</span></span>
    
## <a name="mapping-contosos-business-needs-to-microsofts-cloud-offerings"></a><span data-ttu-id="fb496-130">Asignación de las necesidades de negocio de Contoso a las ofertas de nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="fb496-130">Mapping Contoso's business needs to Microsoft's cloud offerings</span></span>

<span data-ttu-id="fb496-131">Basándose en un análisis de las ofertas de nube de Microsoft, el departamento de TI de Contoso determinó la asignación siguiente:</span><span class="sxs-lookup"><span data-stu-id="fb496-131">Based on an analysis of Microsoft's cloud offerings, Contoso's IT department determined the following mapping:</span></span>
  
|<span data-ttu-id="fb496-132">**Software como servicio (SaaS)**</span><span class="sxs-lookup"><span data-stu-id="fb496-132">**Software as a Service (SaaS)**</span></span>|<span data-ttu-id="fb496-133">**Plataforma como servicio (PaaS de Azure).**</span><span class="sxs-lookup"><span data-stu-id="fb496-133">**Platform as a Service (Azure PaaS )**</span></span>|<span data-ttu-id="fb496-134">**Infraestructura como servicio (IaaS de Azure).**</span><span class="sxs-lookup"><span data-stu-id="fb496-134">**Infrastructure as a Service (Azure IaaS )**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="fb496-135">**Office 365:** aplicaciones de productividad personal y de grupo principales en la nube.</span><span class="sxs-lookup"><span data-stu-id="fb496-135">**Office 365:** Primary personal and group productivity applications in the cloud.</span></span> <br/> <span data-ttu-id="fb496-136">Necesidades de negocio: 1 3 5</span><span class="sxs-lookup"><span data-stu-id="fb496-136">Business needs: 1 3 5</span></span>  <br/> |<span data-ttu-id="fb496-137">Hospedar sistemas de información y documentos de ventas y soporte técnico mediante aplicaciones basadas en la nube.</span><span class="sxs-lookup"><span data-stu-id="fb496-137">Host sales and support documents and information systems using cloud-based apps.</span></span>  <br/> <span data-ttu-id="fb496-138">Necesidad de negocio: 3</span><span class="sxs-lookup"><span data-stu-id="fb496-138">Business need: 3</span></span>  <br/> |<span data-ttu-id="fb496-139">Mover los sistemas de archivo y heredados a servidores basados en la nube.</span><span class="sxs-lookup"><span data-stu-id="fb496-139">Move archival and legacy systems to cloud-based servers.</span></span>  <br/> <span data-ttu-id="fb496-140">Necesidad de negocio: 5</span><span class="sxs-lookup"><span data-stu-id="fb496-140">Business need: 5</span></span>  <br/> |
|<span data-ttu-id="fb496-p102">**Dynamics 365:** Usar la administración basada en la nube de clientes y proveedores. Quitar la extranet de partners en la red perimetral.</span><span class="sxs-lookup"><span data-stu-id="fb496-p102">**Dynamics 365:** Use cloud-based customer and vendor management. Remove partner extranet in the DMZ. </span></span><br/> <span data-ttu-id="fb496-143">Necesidad de negocio: 2</span><span class="sxs-lookup"><span data-stu-id="fb496-143">Business need: 2</span></span>  <br/> |<span data-ttu-id="fb496-144">Las aplicaciones móviles están basadas en la nube, en lugar de en el centro de datos de París.</span><span class="sxs-lookup"><span data-stu-id="fb496-144">Mobile applications are cloud-based, rather than Paris datacenter-based.</span></span>  <br/> <span data-ttu-id="fb496-145">Necesidades de negocio: 3 4</span><span class="sxs-lookup"><span data-stu-id="fb496-145">Business needs: 3 4</span></span>  <br/> |<span data-ttu-id="fb496-146">Migrar las aplicaciones que se usan poco fuera de los centros de datos locales.</span><span class="sxs-lookup"><span data-stu-id="fb496-146">Migrate low-use apps and data out of on-premises datacenters.</span></span>  <br/> <span data-ttu-id="fb496-147">Necesidad de negocio: 5</span><span class="sxs-lookup"><span data-stu-id="fb496-147">Business need: 5</span></span>  <br/> |
|<span data-ttu-id="fb496-148">**Intune/EMS:** administrar dispositivos iOS y Android.</span><span class="sxs-lookup"><span data-stu-id="fb496-148">**Intune/EMS:** Manage iOS and Android devices.</span></span> <br/> <span data-ttu-id="fb496-149">Necesidad de negocio: 3</span><span class="sxs-lookup"><span data-stu-id="fb496-149">Business need: 3</span></span>  <br/> ||<span data-ttu-id="fb496-150">Agregar almacenamiento y servidores temporales para satisfacer las necesidades de procesamiento de fin de trimestre.</span><span class="sxs-lookup"><span data-stu-id="fb496-150">Add temporary servers and storage for end-of-quarter processing needs.</span></span>  <br/> <span data-ttu-id="fb496-151">Necesidad de negocio: 6</span><span class="sxs-lookup"><span data-stu-id="fb496-151">Business need: 6</span></span>  <br/> |
   
## <a name="see-also"></a><span data-ttu-id="fb496-152">See Also</span><span class="sxs-lookup"><span data-stu-id="fb496-152">See Also</span></span>

[<span data-ttu-id="fb496-153">Contoso en la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="fb496-153">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="fb496-154">Recursos de arquitectura de TI de la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="fb496-154">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="fb496-155">Mapa de ruta de Enterprise Cloud de Microsoft: Recursos para los responsables de decisiones de TI</span><span class="sxs-lookup"><span data-stu-id="fb496-155">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)


