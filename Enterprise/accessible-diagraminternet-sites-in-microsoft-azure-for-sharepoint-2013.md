---
title: Diagrama accesible Sitios de Internet en Microsoft Azure para SharePoint 2013
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 71636974-fb99-487c-ac67-f15e9401acba
description: Este artículo es una versión de texto accesible del diagrama con el nombre Sitios de Internet en Microsoft Azure para SharePoint 2013.
ms.openlocfilehash: cf978dfb95b1f201c342889fc3dda428bb618241
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2019
ms.locfileid: "38028064"
---
# <a name="accessible-diagram---internet-sites-in-microsoft-azure-for-sharepoint-2013"></a><span data-ttu-id="0562a-103">Diagrama accesible: Sitios de Internet en Microsoft Azure para SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="0562a-103">Accessible diagram - Internet sites in Microsoft Azure for SharePoint 2013</span></span>

<span data-ttu-id="0562a-104">**Resumen:** este artículo es una versión de texto accesible del diagrama “Sitios de Internet en Microsoft Azure para SharePoint 2013”.</span><span class="sxs-lookup"><span data-stu-id="0562a-104">**Summary:** This article is an accessible text version of the diagram named Internet sites in Microsoft Azure for SharePoint 2013.</span></span>
  
<span data-ttu-id="0562a-p101">Este póster describe e ilustra cómo los sitios de Internet públicos se benefician de la elasticidad de la nube y de Azure AD para cuentas de clientes. Hay seis diferentes escenarios que describen las ventajas de Azure para los sitios de Internet:</span><span class="sxs-lookup"><span data-stu-id="0562a-p101">This poster describes and illustrates how public-facing Internet sites benefit from cloud elasticity and Azure AD for customer accounts. There are six different scenarios that describe how Internet sites benefit from Azure:</span></span> 
  
- <span data-ttu-id="0562a-107">Diseño y cambio de tamaño de la topología de la granja de servidores.</span><span class="sxs-lookup"><span data-stu-id="0562a-107">Design and size the farm topology.</span></span> 
    
- <span data-ttu-id="0562a-108">Ajuste para Azure.</span><span class="sxs-lookup"><span data-stu-id="0562a-108">Fine-tune for Azure.</span></span> 
    
- <span data-ttu-id="0562a-109">Elección del modelo de Active Directory.</span><span class="sxs-lookup"><span data-stu-id="0562a-109">Choose the Active Directory model.</span></span> 
    
- <span data-ttu-id="0562a-110">Diseño de la administración de identidades, zonas y autenticación.</span><span class="sxs-lookup"><span data-stu-id="0562a-110">Design for identity management, zones, and authentication.</span></span> 
    
- <span data-ttu-id="0562a-111">Diseño de sitios y URL para la publicación entre sitios.</span><span class="sxs-lookup"><span data-stu-id="0562a-111">Design sites and URLs for cross-site publishing.</span></span> 
    
- <span data-ttu-id="0562a-112">Diseño del entorno de Azure.</span><span class="sxs-lookup"><span data-stu-id="0562a-112">Design the Azure environment.</span></span> 
    
## <a name="design-and-size-the-farm-topology"></a><span data-ttu-id="0562a-113">Diseño y cambio de tamaño de la topología de la granja de servidores</span><span class="sxs-lookup"><span data-stu-id="0562a-113">Design and size the farm topology</span></span>

<span data-ttu-id="0562a-114">Use la guía sobre topología, capacidad y rendimiento de SharePoint 2013 que encontrará en TechNet para diseñar la topología de la granja de servidores.</span><span class="sxs-lookup"><span data-stu-id="0562a-114">Use the topology, capacity, and performance guidance for SharePoint 2013 on TechNet to design the farm topology.</span></span> 
  
<span data-ttu-id="0562a-115">Asegúrese de que la granja de servidores que diseñe cumpla los objetivos de capacidad y rendimiento marcados.</span><span class="sxs-lookup"><span data-stu-id="0562a-115">Ensure the farm you design meets the objectives for capacity and performance.</span></span> 
  
### <a name="example-medium-internet-sites-farm-85-page-views-per-second"></a><span data-ttu-id="0562a-116">Ejemplo: Granja de servidores de sitios de Internet de tamaño medio (~85 vistas de página por segundo)</span><span class="sxs-lookup"><span data-stu-id="0562a-116">Example: Medium Internet Sites farm (~85 page views per second)</span></span>

<span data-ttu-id="0562a-117">Esta granja ofrece una topología de granja de servidores de búsqueda de SharePoint 2013 con tolerancia a errores y optimizada para un conjunto de 3.400.000 elementos.</span><span class="sxs-lookup"><span data-stu-id="0562a-117">This farm provides a fault-tolerant SharePoint 2013 search farm topology that is optimized for a corpus that contains 3,400,000 items.</span></span> 
  
<span data-ttu-id="0562a-118">La granja de servidores de ejemplo procesa de 100 a 200 documentos por segundo, en función del idioma, y admite 85 visualizaciones de página por segundo y 100 consultas por segundo.</span><span class="sxs-lookup"><span data-stu-id="0562a-118">The example farm processes 100-200 documents per second, depending on the language, and it accommodates 85 page views per second and 100 queries per second.</span></span> 
  
<span data-ttu-id="0562a-119">El diagrama adjunto muestra una granja de servidores de sitios de Internet de tamaño medio con tres tipos de servidores:</span><span class="sxs-lookup"><span data-stu-id="0562a-119">The accompanying diagram shows a medium internet sites farm with three types of servers:</span></span> 
  
- <span data-ttu-id="0562a-120">Servidores web</span><span class="sxs-lookup"><span data-stu-id="0562a-120">Web servers</span></span> 
    
- <span data-ttu-id="0562a-121">Servidores de aplicaciones</span><span class="sxs-lookup"><span data-stu-id="0562a-121">Application servers</span></span> 
    
- <span data-ttu-id="0562a-122">Servidores de base de datos</span><span class="sxs-lookup"><span data-stu-id="0562a-122">Database servers</span></span> 
    
#### <a name="web-servers"></a><span data-ttu-id="0562a-123">Servidores web</span><span class="sxs-lookup"><span data-stu-id="0562a-123">Web servers</span></span>

<span data-ttu-id="0562a-p102">En la sección de servidores web, hay tres servidores web, el Host A, el Host B y Host C. Cada servidor web contiene una memoria caché distribuida, perfiles de usuario, metadatos administrados y capacidades de procesamiento de consultas. También contienen una réplica de partición de índice que se encuentra en cada servidor.</span><span class="sxs-lookup"><span data-stu-id="0562a-p102">In the web servers section, there are three web servers, Host A, Host B, and Host C. Each web server contains a distributed cache, user profiles, managed metadata, and query processing capabilities. They also contain an index partition replica that is in each server.</span></span> 
  
<span data-ttu-id="0562a-126">Para escalar horizontalmente, agregue otro servidor web con las mismas capacidades, esto permite tener 28 vistas de página por segundo adicionales.</span><span class="sxs-lookup"><span data-stu-id="0562a-126">To scale out, add an additional web server with the same capabilities, which allows for an additional 28 page views per second.</span></span> 
  
#### <a name="application-servers"></a><span data-ttu-id="0562a-127">Servidores de aplicaciones</span><span class="sxs-lookup"><span data-stu-id="0562a-127">Application servers</span></span>

<span data-ttu-id="0562a-p103">En la sección Servidores de aplicaciones, hay tres servidores de aplicaciones, el Host D, el Host E y el Host F. El Host D contiene componentes de procesamiento de rastreo, administración, análisis y contenido. El Host E contiene componentes de procesamiento de rastreo, administración y contenido. El Host F contiene componentes de procesamiento de rastreo y contenido.</span><span class="sxs-lookup"><span data-stu-id="0562a-p103">In the application servers section, there are three application servers, Host D, Host E, and Host F. Host D contains Crawl, Admin, Analytics, and Content processing components. Host E contains Crawl, Admin, and Content processing components. Host F contains Crawl and Content processing components.</span></span> 
  
<span data-ttu-id="0562a-131">Para escalar horizontalmente, agregue un servidor de aplicaciones con un componente de rastreo y un componente de procesamiento de contenido para procesar 40 documentos más por segundo.</span><span class="sxs-lookup"><span data-stu-id="0562a-131">To scale out, add one application server with a crawl component and a content processing component to process an additional 40 documents per second.</span></span> 
  
#### <a name="database-servers"></a><span data-ttu-id="0562a-132">Servidores de bases de datos</span><span class="sxs-lookup"><span data-stu-id="0562a-132">Database servers</span></span>

<span data-ttu-id="0562a-133">En la sección Servidores de bases de datos, hay dos servidores, el Host G y el Host H. Los servidores de bases de datos están en hosts emparejados para brindar tolerancia a errores.</span><span class="sxs-lookup"><span data-stu-id="0562a-133">In the database servers section, there are two servers, Host G and Host H. The database servers are in paired hosts for fault tolerance.</span></span> 
  
<span data-ttu-id="0562a-p104">El Host G contiene todas bases de datos de SharePoint, incluida la base de datos de administración de búsqueda, la base de datos de vínculo, dos bases de datos de rastreo, una base de datos de análisis y el resto de bases de datos de SharePoint. El Host H contiene todas las bases de datos de SharePoint, incluidas copias redundantes de todas las bases de datos que usan clústeres de SQL, creación de reflejo o SQL Server 2012 AlwaysOn.</span><span class="sxs-lookup"><span data-stu-id="0562a-p104">Host G contains all SharePoint database, including Search admin database, Link database, two Crawl databases, an Analytics database, and all other SharePoint databases. Host H contains all SharePoint databases, including redundant copies of all databases using SQL clustering, mirroring, or SQL Server 2012 AlwaysOn.</span></span> 
  
## <a name="fine-tune-for-azure"></a><span data-ttu-id="0562a-136">Ajuste para Azure</span><span class="sxs-lookup"><span data-stu-id="0562a-136">Fine-tune for Azure</span></span>

<span data-ttu-id="0562a-p105">Podría ser necesario ajustar la granja de servidores de SharePoint para los conjuntos de disponibilidad en la plataforma de Azure. Para garantizar la alta disponibilidad de todos los componentes, asegúrese de que los roles de servidor estén configurados todos de forma idéntica.</span><span class="sxs-lookup"><span data-stu-id="0562a-p105">The SharePoint farm might need to be fine-tuned for availability sets in the Azure platform. To ensure high availability of all components, ensure that the server roles are all identically configured.</span></span> 
  
<span data-ttu-id="0562a-139">En el ejemplo de topología del diagrama:</span><span class="sxs-lookup"><span data-stu-id="0562a-139">In the example topology in the diagram:</span></span> 
  
- <span data-ttu-id="0562a-140">Los servidores web y los servidores de bases de datos están configurados de forma idéntica.</span><span class="sxs-lookup"><span data-stu-id="0562a-140">The web servers and the database servers are identically configured.</span></span> 
    
- <span data-ttu-id="0562a-p106">Los tres servidores de aplicaciones no están configurados idénticamente. Estos roles de servidor requieren ajustes para los conjuntos de disponibilidad en Azure.</span><span class="sxs-lookup"><span data-stu-id="0562a-p106">The three application servers are not identically configured. These server roles require fine tuning for availability sets in Azure.</span></span> 
    
### <a name="before"></a><span data-ttu-id="0562a-143">Antes</span><span class="sxs-lookup"><span data-stu-id="0562a-143">Before</span></span>

<span data-ttu-id="0562a-p107">La parte superior del diagrama muestra la granja de servidores de SharePoint antes del ajuste para los conjuntos de disponibilidad en Azure. En el diagrama, los tres servidores de aplicaciones host no están configurados de forma idéntica. El número de componentes queda determinado por los objetivos de rendimiento y capacidad de la granja de servidores. Los tres servidores están configurados como sigue:</span><span class="sxs-lookup"><span data-stu-id="0562a-p107">The top portion of the diagram shows the SharePoint farm before it has been fine-tuned for availability sets in Azure. In the diagram, the three host application servers are not identically configured. The number of components is determined by the performance and capacity targets for the farm. The three servers are configured as follows:</span></span> 
  
- <span data-ttu-id="0562a-148">El servidor de aplicaciones Host D está configurado con los roles de procesamiento de rastreo, administración, análisis y contenido.</span><span class="sxs-lookup"><span data-stu-id="0562a-148">Host D application server is configured with Crawl, Admin, Analytics, and Content processing roles.</span></span> 
    
- <span data-ttu-id="0562a-149">El servidor de aplicaciones Host E está configurado con los roles de procesamiento de rastreo, administración y contenido.</span><span class="sxs-lookup"><span data-stu-id="0562a-149">Host E application server is configured with Crawl, Admin, and Content processing roles.</span></span> 
    
- <span data-ttu-id="0562a-150">El servidor de aplicaciones Host F está configurado con los roles de procesamiento de rastreo y contenido.</span><span class="sxs-lookup"><span data-stu-id="0562a-150">Host F application server is configured with Crawl and Content processing roles.</span></span> 
    
### <a name="after"></a><span data-ttu-id="0562a-151">Después</span><span class="sxs-lookup"><span data-stu-id="0562a-151">After</span></span>

<span data-ttu-id="0562a-p108">Esta parte del diagrama muestra la granja de servidores de SharePoint después del ajuste para los conjuntos de disponibilidad de Azure. Para adaptar esta arquitectura para Azure, replicaremos los cuatro componentes en los tres servidores. Esto incrementa el número de componentes más allá de lo necesario para obtener el rendimiento y capacidad buscados. A cambio, este diseño garantiza la alta disponibilidad de los cuatro componentes en la plataforma de Azure cuando estas tres máquinas virtuales están asignadas a un conjunto de disponibilidad.</span><span class="sxs-lookup"><span data-stu-id="0562a-p108">This part of the diagram shows the SharePoint farm after it has been fine-tuned for availability sets in Azure. To adapt this architecture for Azure, we'll replicate the four components across all three servers. This increases the number of components beyond what is necessary for performance and capacity. The tradeoff is that this design ensures high availability of all four components in the Azure platform when these three virtual machines are assigned to an availability set.</span></span> 
  
<span data-ttu-id="0562a-156">Los tres servidores están configurados para contar con los roles de procesamiento de rastreo, administración, análisis y contenido.</span><span class="sxs-lookup"><span data-stu-id="0562a-156">The three servers are configured to all have the Crawl, Admin, Analytics, and Content processing roles.</span></span> 
  
## <a name="choose-the-active-directory-model"></a><span data-ttu-id="0562a-157">Elección del modelo de Active Directory</span><span class="sxs-lookup"><span data-stu-id="0562a-157">Choose the Active Directory model</span></span>

<span data-ttu-id="0562a-p109">Todas las soluciones de SharePoint requieren Servicios de dominio de Windows Active Directory (AD DS). Actualmente, existen dos opciones para las soluciones de SharePoint en Azure.</span><span class="sxs-lookup"><span data-stu-id="0562a-p109">All SharePoint solutions require Windows Active Directory Domain Services (AD DS). At this time, there are two options for SharePoint solutions in Azure.</span></span> 
  
- <span data-ttu-id="0562a-p110">Opción 1: Dominio dedicado. Puede implementar un dominio dedicado y aislado en Azure para obtener compatibilidad para una granja de servidores de SharePoint. Esta es una buena opción para sitios de Internet públicos.</span><span class="sxs-lookup"><span data-stu-id="0562a-p110">Option 1: Dedicated domain — You can deploy a dedicated and isolated domain to Azure to support a SharePoint farm. This is a good choice for public-facing Internet sites.</span></span> 
    
- <span data-ttu-id="0562a-p111">Opción 2: Extender el dominio local a través de una conexión VPN sitio a sitio. Cuando el dominio local se extiende a través de una conexión VPN sitio a sitio, los usuarios tienen acceso a la granja de servidores de SharePoint como si estuvieran hospedados localmente. Puede aprovechar las implementaciones existentes de Active Directory y DNS.</span><span class="sxs-lookup"><span data-stu-id="0562a-p111">Option 2: Extend the on-premises domain through a site-to-site VPN connection. When you extend the on-premises domain through a site-to-site VPN connection, users access the SharePoint farm as if it were hosted on-premises. You can take advantage of your existing Active Directory and DNS implementations.</span></span> 
    
## <a name="design-for-identity-management-zones-and-authentication"></a><span data-ttu-id="0562a-165">Diseño de la administración de identidades, zonas y autenticación</span><span class="sxs-lookup"><span data-stu-id="0562a-165">Design for identity management, zones, and authentication</span></span>

### <a name="design-for-accounts-and-authentication"></a><span data-ttu-id="0562a-166">Diseño de cuentas y autenticación</span><span class="sxs-lookup"><span data-stu-id="0562a-166">Design for accounts and authentication</span></span>

<span data-ttu-id="0562a-167">Determine cómo se administrarán las cuentas y qué tipo de autenticación se usará.</span><span class="sxs-lookup"><span data-stu-id="0562a-167">Determine how accounts will be managed and which type of authentication will be used.</span></span> 
  
#### <a name="accounts-for-site-developers-and-authors"></a><span data-ttu-id="0562a-168">Cuentas para desarrolladores y creadores de sitios</span><span class="sxs-lookup"><span data-stu-id="0562a-168">Accounts for site developers and authors</span></span>

- <span data-ttu-id="0562a-169">Agregue las cuentas al dominio en Azure.</span><span class="sxs-lookup"><span data-stu-id="0562a-169">Add accounts to the domain in Azure.</span></span> 
    
- <span data-ttu-id="0562a-170">Use los servicios de federación de Active Directory (AD FS) locales para federar las cuentas internas al dominio en Azure.</span><span class="sxs-lookup"><span data-stu-id="0562a-170">Use Active Directory Federation Services (AD FS) on premises to federate the internal accounts to the domain in Azure.</span></span> 
    
- <span data-ttu-id="0562a-171">Si el diseño incluye una conexión VPN sitio a sitio, use las cuentas internas.</span><span class="sxs-lookup"><span data-stu-id="0562a-171">If the design includes a site-to-site VPN connection, use the internal accounts.</span></span> 
    
#### <a name="accounts-for-customers"></a><span data-ttu-id="0562a-172">Cuentas de clientes</span><span class="sxs-lookup"><span data-stu-id="0562a-172">Accounts for customers</span></span>

- <span data-ttu-id="0562a-173">Use Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="0562a-173">Use Azure Active Directory.</span></span> 
    
- <span data-ttu-id="0562a-174">Use un proveedor basado en SAML diferente.</span><span class="sxs-lookup"><span data-stu-id="0562a-174">Use a different SAML-based provider.</span></span> 
    
### <a name="design-for-zones"></a><span data-ttu-id="0562a-175">Diseño de zonas</span><span class="sxs-lookup"><span data-stu-id="0562a-175">Design for zones</span></span>

<span data-ttu-id="0562a-176">En SharePoint 2013, la administración de identidades se incluye en la configuración de las zonas y la autenticación.</span><span class="sxs-lookup"><span data-stu-id="0562a-176">In SharePoint 2013, identity management is factored into the configuration of zones and authentication.</span></span> 
  
<span data-ttu-id="0562a-177">Este diseño distingue claramente entre las cuentas de los clientes y las demás cuentas.</span><span class="sxs-lookup"><span data-stu-id="0562a-177">This design provides clear separation of customer accounts from all other accounts.</span></span> 
  
- <span data-ttu-id="0562a-178">Use este diseño si desea que las cuentas de clientes se traten de forma completamente distinta a como se tratan las cuentas internas de creadores y desarrolladores de sitios.</span><span class="sxs-lookup"><span data-stu-id="0562a-178">Use this design if you want customer accounts to be treated entirely different from the internal accounts for authors and site developers.</span></span> 
    
- <span data-ttu-id="0562a-179">Mediante el uso de este diseño, puede usar directivas de zona para limitar las acciones del cliente dentro de una aplicación web.</span><span class="sxs-lookup"><span data-stu-id="0562a-179">By using this design, you can use zone policies to limit customer actions within a web application.</span></span> 
    
- <span data-ttu-id="0562a-180">Con este diseño se obtienen direcciones URL diferentes para las cuentas de clientes y para las cuentas internas.</span><span class="sxs-lookup"><span data-stu-id="0562a-180">This design results in different URLs for customer accounts and internal accounts.</span></span> 
    
<span data-ttu-id="0562a-181">En este ejemplo:</span><span class="sxs-lookup"><span data-stu-id="0562a-181">In this example:</span></span> 
  
- <span data-ttu-id="0562a-182">Configure la zona predeterminada para las cuentas internas.</span><span class="sxs-lookup"><span data-stu-id="0562a-182">Configure the default zone for internal accounts.</span></span> 
    
- <span data-ttu-id="0562a-p112">Configure la zona de extranet para el acceso autenticado de clientes. Use Azure Active Directory (AD) para las cuentas de cliente o use un proveedor basado en SAML diferente.</span><span class="sxs-lookup"><span data-stu-id="0562a-p112">Configure the extranet zone for customer authenticated access. Use Azure Active Directory (AD) for customer accounts, or use a different SAML-based provider.</span></span> 
    
- <span data-ttu-id="0562a-185">Configure la zona de Internet para el acceso anónimo.</span><span class="sxs-lookup"><span data-stu-id="0562a-185">Configure the Internet zone for anonymous access.</span></span> 
    
<span data-ttu-id="0562a-186">No use un diseño de dos zonas en el que todos los usuarios autenticados estén configurados para usar la zona predeterminada.</span><span class="sxs-lookup"><span data-stu-id="0562a-186">Don't use a two-zone design in which all authenticated users are configured to use the default zone.</span></span> 
  
<span data-ttu-id="0562a-187">El diagrama adjunto muestra un diseño de tres zonas que distingue entre cuentas internas y de clientes.</span><span class="sxs-lookup"><span data-stu-id="0562a-187">The accompanying diagram shows a three-zone design with separation of internal and customer accounts.</span></span> 
  
<span data-ttu-id="0562a-p113">Los visitantes y clientes tienen acceso al inquilino de Azure AD en la granja de servidores de SharePoint 2013 a través de aplicaciones web en una de dos zonas. Las dos zonas son:</span><span class="sxs-lookup"><span data-stu-id="0562a-p113">Visitors and customers access the Azure AD Tenant in the SharePoint 2013 farm through web applications in one of two zones. The two zones include:</span></span> 
  
- <span data-ttu-id="0562a-190">Zona: Internet para los usuarios anónimos</span><span class="sxs-lookup"><span data-stu-id="0562a-190">Zone: Internet for anonymous users</span></span> 
    
- <span data-ttu-id="0562a-191">Zona: Extranet para los usuarios autenticados</span><span class="sxs-lookup"><span data-stu-id="0562a-191">Zone: Extranet for authenticated users</span></span> 
    
<span data-ttu-id="0562a-p114">Los usuarios con cuentas internas tienen acceso al inquilino de Azure Active Directory desde de AD DS y AD FS en el entorno local a través del túnel de VPN a Azure AD. La zona predeterminada proporciona la autenticación de Windows (NTLM).</span><span class="sxs-lookup"><span data-stu-id="0562a-p114">Users with internal accounts access the Azure Active Directory Tenant from AD DS and AD FS in the on-premises environment through the VPN tunnel to Azure AD. The Default zone provides Windows Authentication (NTLM).</span></span> 
  
### <a name="design-for-connecting-to-azure-ad"></a><span data-ttu-id="0562a-194">Diseño para la conexión a Azure AD</span><span class="sxs-lookup"><span data-stu-id="0562a-194">Design for connecting to Azure AD</span></span>

 <span data-ttu-id="0562a-p115">Azure AD proporciona capacidades de control de acceso y administración de identidades para servicios en la nube. Las capacidades incluyen almacenamiento basado en la nube para los datos del directorio y un conjunto principal de servicios de identidad (que comprende los procesos de inicio de sesión de usuarios, los servicios de autenticación y AD FS). Los servicios de identidad que se incluyen con Azure AD se integran fácilmente en las implementaciones locales de AD DS y son totalmente compatibles con los proveedores de identidades de terceros.</span><span class="sxs-lookup"><span data-stu-id="0562a-p115">Azure AD provides identity management and access control capabilities for cloud services. Capabilities include a cloud-based store for directory data and a core set of identity services, including user logon processes, authentication services, and AD FS. The identity services that are included with Azure AD easily integrate with your on-premises AD DS deployments and fully support third-party identity providers.</span></span>
  
<span data-ttu-id="0562a-198">El diagrama adjunto muestra el siguiente escenario:</span><span class="sxs-lookup"><span data-stu-id="0562a-198">The accompanying diagram shows the following scenario:</span></span> 
  
<span data-ttu-id="0562a-199">Al integrar SharePoint 2013 con Azure Active Directory, el servicio de Control de acceso (ACS) de Azure cumple dos propósitos:</span><span class="sxs-lookup"><span data-stu-id="0562a-199">When integrating SharePoint 2013 with Azure Active Directory, an Azure Access Control Service (ACS) serves two purposes:</span></span> 
  
-  <span data-ttu-id="0562a-p116">Azure AD usa SAML 2.0 y SharePoint únicamente funciona con SAML 1.1. ACS admite ambos formatos y actúa como intermediario para transformar los formatos de token entre SharePoint y Azure AD.</span><span class="sxs-lookup"><span data-stu-id="0562a-p116">Azure AD uses SAML 2.0, and SharePoint only works with SAML 1.1. ACS understands both formats and serves as the intermediary to transform the token formats between SharePoint and Azure AD.</span></span>
    
- <span data-ttu-id="0562a-202">ACS reemplaza la necesidad del servicio de token de seguridad del proveedor de identidades (STS de IP) para este escenario de SAML.</span><span class="sxs-lookup"><span data-stu-id="0562a-202">ACS replaces the need for the identity provider security token service (IP-STS) for this SAML scenario.</span></span> 
    
<span data-ttu-id="0562a-203">Para obtener más información, consulte el tema sobre configuración de Azure AD con SharePoint 2013 en la biblioteca de TechNet.</span><span class="sxs-lookup"><span data-stu-id="0562a-203">For more information, see Configure Azure AD with SharePoint 2013 in the TechNet library.</span></span> 
  
## <a name="design-sites-and-urls-for-cross-site-publishing"></a><span data-ttu-id="0562a-204">Diseño de sitios y URL para la publicación entre sitios</span><span class="sxs-lookup"><span data-stu-id="0562a-204">Design sites and URLs for cross-site publishing</span></span>

<span data-ttu-id="0562a-205">Se recomienda usar un diseño de una aplicación web para los escenarios de publicación.</span><span class="sxs-lookup"><span data-stu-id="0562a-205">A one web-application design is recommended for publishing scenarios.</span></span> 
  
- <span data-ttu-id="0562a-206">Las funciones tanto de creación como de publicación de sitios están en la misma aplicación web.</span><span class="sxs-lookup"><span data-stu-id="0562a-206">Both authoring and publishing sites are in the same web application.</span></span> 
    
- <span data-ttu-id="0562a-207">La publicación en varios sitios se usa para publicar activos.</span><span class="sxs-lookup"><span data-stu-id="0562a-207">Cross-site publishing is used to publish assets.</span></span> 
    
<span data-ttu-id="0562a-208">Use colecciones de sitios con nombre de host y basados en rutas de acceso.</span><span class="sxs-lookup"><span data-stu-id="0562a-208">Use path-based and host-named site collections.</span></span> 
  
- <span data-ttu-id="0562a-p117">Es necesario contar con una colección de sitios raíz. Cree este sitio como un sitio basado en la ruta de acceso.</span><span class="sxs-lookup"><span data-stu-id="0562a-p117">A root site collection is a requirement. Create this site as a path-based site.</span></span> 
    
- <span data-ttu-id="0562a-211">Cree el resto de las colecciones de sitios como colecciones con nombre de host.</span><span class="sxs-lookup"><span data-stu-id="0562a-211">Create all other site collections as host-named site collections.</span></span> 
    
<span data-ttu-id="0562a-212">Direcciones URL de aplicaciones web y sitios raíz</span><span class="sxs-lookup"><span data-stu-id="0562a-212">Web application and root site URLs</span></span> 
  
- <span data-ttu-id="0562a-p118">Use un nombre interno para la URL de la aplicación web. SharePoint usa el nombre de la máquina local como nombre predeterminado a menos que se especifique un nombre distinto. Puede usar un nombre de dominio reservado para el entorno de red interno.</span><span class="sxs-lookup"><span data-stu-id="0562a-p118">Use an internal name for the web application URL. SharePoint uses the local machine name as the default name unless a different name is specified. You can use a domain name that is reserved for the internal network environment.</span></span> 
    
- <span data-ttu-id="0562a-p119">SharePoint asigna un número de puerto no estándar al momento de crear la aplicación web. Use este número de puerto en lugar del puerto 80 o el puerto 443. O use un número de puerto diferente pero que no sea estándar.</span><span class="sxs-lookup"><span data-stu-id="0562a-p119">SharePoint assigns a nonstandard port number when the web application is created. Use this port number instead of port 80 or port 443. Or use a different but nonstandard port number.</span></span> 
    
- <span data-ttu-id="0562a-219">Use el mismo nombre y número de puerto que usó para la colección de sitios raíz, que es una colección de sitios basados en rutas de acceso.</span><span class="sxs-lookup"><span data-stu-id="0562a-219">Use the same name and port number for the root site collection, which is a path-based site collection.</span></span> 
    
<span data-ttu-id="0562a-p120">El diagrama adjunto muestra servicios para grupos de aplicaciones, como el servicio de búsqueda, interactuando con la colección de sitios que usan aplicaciones web. Las colecciones de sitios mostradas incluyen:</span><span class="sxs-lookup"><span data-stu-id="0562a-p120">The accompanying diagram shows application pool services such as Search interacting with site collections using web applications. The site collections shown include:</span></span> 
  
- <span data-ttu-id="0562a-222">Una colección de sitios basados en la ruta de acceso que se encuentra en https://internal:8000 (sitio raíz).</span><span class="sxs-lookup"><span data-stu-id="0562a-222">Path-based site collection located at https://internal:8000 (root site).</span></span> 
    
- <span data-ttu-id="0562a-223">Rastreo: Colecciones de sitios con nombre de host ubicadas en una dirección como https://authoring.contoso.com:8000.</span><span class="sxs-lookup"><span data-stu-id="0562a-223">Crawl: Host-named site collections located at an address such as https://authoring.contoso.com:8000.</span></span> 
    
- <span data-ttu-id="0562a-224">Consultas: Dos colecciones de sitios independientes con nombre de host que se encuentran en direcciones como:</span><span class="sxs-lookup"><span data-stu-id="0562a-224">Queries: 2 separate Host-named site collections located at addresses such as:</span></span> 
    
  - https://www.contoso.com 
    
  - https://secure.contoso.com 
    
  - https://www.contoso.com:8000 
    
  - https://assets.contoso.com 
    
  - https://secureassets.contoso.com 
    
  - https://assets.contoso.com:8000 
    
## <a name="design-the-azure-environment"></a><span data-ttu-id="0562a-225">Diseño del entorno de Azure</span><span class="sxs-lookup"><span data-stu-id="0562a-225">Design the Azure environment</span></span>

<span data-ttu-id="0562a-226">Esta arquitectura de ejemplo incluye los siguientes elementos:</span><span class="sxs-lookup"><span data-stu-id="0562a-226">This example architecture includes the following elements:</span></span> 
  
- <span data-ttu-id="0562a-227">Una conexión VPN sitio a sitio que es opcional y extiende Windows AD DS local y el entorno de DNS local a la red virtual en Azure.</span><span class="sxs-lookup"><span data-stu-id="0562a-227">A site-to-site VPN connection is optional and extends the on-premises Windows AD DS and DNS environment to the virtual network in Azure.</span></span> 
    
- <span data-ttu-id="0562a-228">Opcionalmente, puede usar un dominio dedicado en Azure para la compatibilidad con la granja de servidores de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="0562a-228">Optionally, use a dedicated domain in Azure to support the SharePoint farm.</span></span> 
    
- <span data-ttu-id="0562a-229">Los servidores se dividen entre los servicios en la nube de Azure según su rol.</span><span class="sxs-lookup"><span data-stu-id="0562a-229">Servers are split across Azure cloud services based on role.</span></span> 
    
- <span data-ttu-id="0562a-230">Conjuntos de disponibilidad que aseguran la alta disponibilidad de los roles de servidor configurados de forma idéntica.</span><span class="sxs-lookup"><span data-stu-id="0562a-230">Availability sets ensure high availability of identically configured server roles.</span></span> 
    
<span data-ttu-id="0562a-231">Para obtener más información, consulte el artículo de TechNet sobre arquitecturas de Azure para soluciones de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="0562a-231">For more information, see the following article on TechNet: Azure Architectures for SharePoint Solutions.</span></span> 
  
<span data-ttu-id="0562a-232">El diagrama adjunto muestra un ejemplo de un entorno local conectado con una red virtual de Azure.</span><span class="sxs-lookup"><span data-stu-id="0562a-232">The accompanying diagram shows an example of an on-premises environment connecting with an Azure virtual network.</span></span> 
  
<span data-ttu-id="0562a-233">En el entorno local, que es un elemento opcional del entorno de Azure, se incluyen los siguientes componentes:</span><span class="sxs-lookup"><span data-stu-id="0562a-233">Included in the on-premises environment, which is an optional element of the Azure environment, are the following components:</span></span> 
  
- <span data-ttu-id="0562a-234">RRAS de Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="0562a-234">Windows Server 2012 RRAS</span></span> 
    
- <span data-ttu-id="0562a-235">AD DS</span><span class="sxs-lookup"><span data-stu-id="0562a-235">AD DS</span></span> 
    
- <span data-ttu-id="0562a-236">Una puerta de enlace de VPN desde Windows Server y AD DS a la subred de la puerta de enlace de VPN activa</span><span class="sxs-lookup"><span data-stu-id="0562a-236">A VPN gateway from Windows Server and AD DS to the Active VPN Gateway subnet</span></span> 
    
<span data-ttu-id="0562a-237">El entorno de red virtual de Azure incluye los siguientes componentes:</span><span class="sxs-lookup"><span data-stu-id="0562a-237">The Azure virtual network environment includes the following components:</span></span> 
  
- <span data-ttu-id="0562a-238">La subred de la puerta de enlace de VPN activa (superpuesta con el entorno local, si es aplicable)</span><span class="sxs-lookup"><span data-stu-id="0562a-238">The Active VPN Gateway subnet (overlapping with the on-premises environment, if applicable)</span></span> 
    
- <span data-ttu-id="0562a-239">Un servicio en la nube que incluye un conjunto de disponibilidad de AD DS y DNS (dos servidores)</span><span class="sxs-lookup"><span data-stu-id="0562a-239">Cloud service that includes AD DS and DNS availability set (two servers)</span></span> 
    
- <span data-ttu-id="0562a-240">Un servicio en la nube que incluye el conjunto de disponibilidad del servidor front-end (tres servidores de SharePoint) y el conjunto de disponibilidad del servidor de aplicaciones (tres servidores de SharePoint)</span><span class="sxs-lookup"><span data-stu-id="0562a-240">Cloud service that include the front-end server availability set (three SharePoint servers) and the App server availability set (three SharePoint servers)</span></span> 
    
- <span data-ttu-id="0562a-241">Un servicio de nube que contiene dos conjuntos de disponibilidad de bases de datos</span><span class="sxs-lookup"><span data-stu-id="0562a-241">Cloud service that contains two database availability sets</span></span> 
    

