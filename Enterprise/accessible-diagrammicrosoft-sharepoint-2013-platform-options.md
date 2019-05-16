---
title: Diagrama accesible Opciones de plataformas de Microsoft SharePoint 2013
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b88200bf-ced0-4ae6-bbe5-5517377d1be1
description: Este artículo es una versión de texto accesible del diagrama Opciones de plataforma para Microsoft SharePoint 2013.
ms.openlocfilehash: 4a0b068ffb8abbe11c2286f3daa70c5f62295425
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068606"
---
# <a name="accessible-diagram---microsoft-sharepoint-2013-platform-options"></a><span data-ttu-id="d794a-103">Diagrama accesible: Opciones de plataformas de Microsoft SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="d794a-103">Accessible diagram - Microsoft SharePoint 2013 Platform Options</span></span>

<span data-ttu-id="d794a-104">**Resumen:** este artículo es una versión de texto accesible del diagrama “Opciones de plataforma para Microsoft SharePoint 2013”.</span><span class="sxs-lookup"><span data-stu-id="d794a-104">**Summary:** This article is an accessible text version of the diagram named Microsoft SharePoint 2013 Platform Options.</span></span>
  
<span data-ttu-id="d794a-105">Todo lo que los arquitectos y los responsables de decisiones empresariales necesitan saber sobre Office 365, Microsoft Azure y las implementaciones locales.</span><span class="sxs-lookup"><span data-stu-id="d794a-105">What business decision makers (BDMs) and architects need to know about Office 365, Microsoft Azure, and on-premises deployments.</span></span> 
  
<span data-ttu-id="d794a-106">Este póster tiene dos secciones:</span><span class="sxs-lookup"><span data-stu-id="d794a-106">This poster has two sections:</span></span> 
  
- <span data-ttu-id="d794a-107">Una comparación de cuatro implementaciones diferentes de SharePoint 2013: SharePoint en Office 365, un híbrido de Office 365 con una implementación local de SharePoint 2013, Azure y una implementación local de SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="d794a-107">A comparison of four different deployments for SharePoint 2013: SharePoint in Office 365, a hybrid of Office 365 with an on-premises deployment of SharePoint 2013, Azure, and an on-premises deployment of SharePoint 2013.</span></span> 
    
- <span data-ttu-id="d794a-108">Una descripción de tres cargas de trabajo típicas para pasar a Azure.</span><span class="sxs-lookup"><span data-stu-id="d794a-108">A description of three typical workloads to move to Azure.</span></span> 
    
## <a name="comparison-of-four-different-deployments-for-the-sharepoint-2013-platform"></a><span data-ttu-id="d794a-109">Comparación de cuatro implementaciones diferentes para la plataforma de SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="d794a-109">Comparison of four different deployments for the SharePoint 2013 platform</span></span>

<span data-ttu-id="d794a-110">La comparación proporciona información sobre cada opción de implementación relacionada con las siguientes áreas:</span><span class="sxs-lookup"><span data-stu-id="d794a-110">The comparison provides information about each deployment option related to the following areas:</span></span> 
  
- <span data-ttu-id="d794a-111">Información general sobre las diferentes características de implementación</span><span class="sxs-lookup"><span data-stu-id="d794a-111">An overview of the different deployment features</span></span> 
    
- <span data-ttu-id="d794a-112">¿Para qué es más adecuado cada tipo de implementación?</span><span class="sxs-lookup"><span data-stu-id="d794a-112">What each type of deployment is best for</span></span> 
    
- <span data-ttu-id="d794a-113">Requisitos de licencia</span><span class="sxs-lookup"><span data-stu-id="d794a-113">License requirements</span></span> 
    
- <span data-ttu-id="d794a-114">Tareas de arquitectura necesarias para implementar</span><span class="sxs-lookup"><span data-stu-id="d794a-114">Architecture tasks required to implement</span></span> 
    
- <span data-ttu-id="d794a-115">Responsabilidades de los profesionales de TI para la implementación</span><span class="sxs-lookup"><span data-stu-id="d794a-115">IT pro responsibilities for implementation</span></span> 
    
### <a name="overview"></a><span data-ttu-id="d794a-116">Información general</span><span class="sxs-lookup"><span data-stu-id="d794a-116">Overview</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="d794a-117">SharePoint 2013 en Office 365</span><span class="sxs-lookup"><span data-stu-id="d794a-117">SharePoint 2013 in Office 365</span></span>

<span data-ttu-id="d794a-118">Aumente su eficiencia y optimice los costos con los planes multiempresa de Office 365.</span><span class="sxs-lookup"><span data-stu-id="d794a-118">Gain efficiency and optimize for cost with Office 365 multitenant plans.</span></span> 
  
<span data-ttu-id="d794a-119">El diagrama adjunto muestra SharePoint Online con un inquilino de Azure Active Directory que sincroniza nombres de cuentas y contraseñas entre el entorno local de Active Directory y el inquilino de Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="d794a-119">The accompanying diagram shows SharePoint Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span> 
  
<span data-ttu-id="d794a-120">Descripción de las características:</span><span class="sxs-lookup"><span data-stu-id="d794a-120">Description of features:</span></span> 
  
- <span data-ttu-id="d794a-121">Software como servicio (SaaS). </span><span class="sxs-lookup"><span data-stu-id="d794a-121">Software as a Service (SaaS).</span></span> 
    
- <span data-ttu-id="d794a-122">El amplio conjunto de características siempre está actualizado.</span><span class="sxs-lookup"><span data-stu-id="d794a-122">Rich feature set is always up to date.</span></span> 
    
- <span data-ttu-id="d794a-123">Incluye un inquilino de Azure Active Directory (se puede usar con otras aplicaciones).</span><span class="sxs-lookup"><span data-stu-id="d794a-123">Includes an Azure Active Directory tenant (can be used with other applications).</span></span> 
    
- <span data-ttu-id="d794a-124">La integración de directorios incluye la sincronización de nombres de cuentas y contraseñas entre el entorno de Active Directory local y el inquilino de Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="d794a-124">Directory integration includes synchronizing account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span> 
    
- <span data-ttu-id="d794a-125">Si se requiere inicio de sesión único (SSO), se pueden implementar los Servicios de federación de Active Directory (AD FS).</span><span class="sxs-lookup"><span data-stu-id="d794a-125">If single sign-on (SSO) is a requirement, Active Directory Federation Services (AD FS) can be implemented.</span></span> 
    
- <span data-ttu-id="d794a-126">Comunicación con cliente por Internet mediante acceso cifrado y con autenticación (puerto 443).</span><span class="sxs-lookup"><span data-stu-id="d794a-126">Client communication over the Internet through encrypted and authenticated access (port 443).</span></span> 
    
- <span data-ttu-id="d794a-127">La migración de datos se limita a lo que se puede cargar por Internet.</span><span class="sxs-lookup"><span data-stu-id="d794a-127">Data migration is limited to what can be uploaded over the Internet.</span></span> 
    
- <span data-ttu-id="d794a-128">Personalizaciones: Aplicaciones para Office, SharePoint y SharePoint Designer 2013.</span><span class="sxs-lookup"><span data-stu-id="d794a-128">Customizations: Apps for Office, SharePoint, and SharePoint Designer 2013.</span></span> 
    
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="d794a-129">Implementación híbrida con Office 365</span><span class="sxs-lookup"><span data-stu-id="d794a-129">Hybrid with Office 365</span></span>

<span data-ttu-id="d794a-130">Combine las ventajas de Office 365 con una implementación local de SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="d794a-130">Combine the benefits of Office 365 with an on-premises deployment of SharePoint 2013.</span></span> 
  
<span data-ttu-id="d794a-131">En el diagrama adjunto se muestra Office 365 con SharePoint Online usando Servicios de conectividad empresarial (BCS) para conectarse a una granja de SharePoint Server 2013 local.</span><span class="sxs-lookup"><span data-stu-id="d794a-131">The accompanying diagram shows Office 365 with SharePoint Online using Business Connectivity Services (BCS) to connect to an on-premises SharePoint Server 2013 farm.</span></span> 
  
<span data-ttu-id="d794a-132">Elija cuál de las siguientes características desea integrar:</span><span class="sxs-lookup"><span data-stu-id="d794a-132">Choose which of the following features to integrate:</span></span> 
  
<span data-ttu-id="d794a-133">SharePoint Search</span><span class="sxs-lookup"><span data-stu-id="d794a-133">SharePoint Search</span></span> 
  
- <span data-ttu-id="d794a-134">Los usuarios pueden ver los resultados de búsqueda de los dos entornos.</span><span class="sxs-lookup"><span data-stu-id="d794a-134">Users can see search results from both environments.</span></span> 
    
- <span data-ttu-id="d794a-135">Los usuarios de la extranet pueden iniciar sesión de forma remota con una cuenta de Active Directory local y usar todas las funciones híbridas disponibles.</span><span class="sxs-lookup"><span data-stu-id="d794a-135">Extranet users can remotely log on with an on-premises Active Directory account and use all available hybrid functionality.</span></span> 
    
<span data-ttu-id="d794a-136">BCS</span><span class="sxs-lookup"><span data-stu-id="d794a-136">BCS</span></span>
  
<span data-ttu-id="d794a-p101">De SharePoint Online: los usuarios pueden realizar operaciones de lectura y escritura. El servicio BCS se conecta a una granja de SharePoint Server 2013 local. El servicio BCS configurado en la granja local negocia la conexión con los extremos locales del servicio OData.</span><span class="sxs-lookup"><span data-stu-id="d794a-p101">From SharePoint Online: Users can perform both read and write operations. The BCS service connects to an on-premises SharePoint Server 2013 farm. The BCS service configured on the on-premises farm brokers the connection to on-premises OData Service endpoints.</span></span> 
  
<span data-ttu-id="d794a-140">Duet Enterprise Online</span><span class="sxs-lookup"><span data-stu-id="d794a-140">Duet Enterprise Online</span></span> 
  
<span data-ttu-id="d794a-141">Desde SharePoint Online, los usuarios pueden realizar operaciones de lectura y escritura en un sistema SAP local.</span><span class="sxs-lookup"><span data-stu-id="d794a-141">From SharePoint Online, users can perform read and write operations against an on-premises SAP system.</span></span> 
  
#### <a name="azure"></a><span data-ttu-id="d794a-142">Azure</span><span class="sxs-lookup"><span data-stu-id="d794a-142">Azure</span></span>

<span data-ttu-id="d794a-143">Aproveche las ventajas que le ofrece la nube a la vez que mantiene el control total sobre la plataforma y las funciones.</span><span class="sxs-lookup"><span data-stu-id="d794a-143">Take advantage of the cloud while maintaining full control of the platform and features.</span></span> 
  
<span data-ttu-id="d794a-144">En el diagrama adjunto se muestra Azure, que contiene dos servicios en la nube, una granja de SharePoint 2013 y Windows Server Active Directory con DNS; se conecta con los usuarios a través de Internet o se conecta a una implementación local de Active Directory mediante un túnel VPN.</span><span class="sxs-lookup"><span data-stu-id="d794a-144">The accompanying diagram shows Azure, which contains two cloud services, a SharePoint 2013 farm, and Windows Server Active Directory with DNS connecting to users over the Internet or connecting to on-premises Active Directory via VPN tunnel.</span></span> 
  
<span data-ttu-id="d794a-145">Entre las características se incluyen:</span><span class="sxs-lookup"><span data-stu-id="d794a-145">Features include:</span></span> 
  
-  <span data-ttu-id="d794a-146">Azure es una plataforma que ofrece la infraestructura y los servicios de aplicaciones necesarios para hospedar una granja de SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="d794a-146">Azure is a platform that provides the infrastructure and app services needed to host a SharePoint 2013 farm.</span></span>
    
- <span data-ttu-id="d794a-147">Servicios de infraestructura.</span><span class="sxs-lookup"><span data-stu-id="d794a-147">Infrastructure Services.</span></span> 
    
- <span data-ttu-id="d794a-148">Mejor plataforma en la nube nativa para SQL Server y SharePoint.</span><span class="sxs-lookup"><span data-stu-id="d794a-148">Best native cloud platform for SQL Server and SharePoint.</span></span> 
    
- <span data-ttu-id="d794a-149">Los recursos informáticos están disponibles prácticamente de inmediato, sin concesiones.</span><span class="sxs-lookup"><span data-stu-id="d794a-149">Computing resources are available almost immediately with no commitment.</span></span> 
    
- <span data-ttu-id="d794a-150">Dé prioridad a las aplicaciones, en lugar de los centros de datos y las infraestructuras.</span><span class="sxs-lookup"><span data-stu-id="d794a-150">Focus on applications, instead of datacenters and infrastructure.</span></span> 
    
- <span data-ttu-id="d794a-151">Entornos de desarrollo y de pruebas económicos.</span><span class="sxs-lookup"><span data-stu-id="d794a-151">Inexpensive development and test environments.</span></span> 
    
- <span data-ttu-id="d794a-152">Es posible acceder a las soluciones de SharePoint desde Internet o bien únicamente desde un entorno corporativo mediante un túnel VPN de sitio a sitio.</span><span class="sxs-lookup"><span data-stu-id="d794a-152">SharePoint solutions can be accessible from the Internet or accessible only from a corporate environment through a site-to-site VPN tunnel.</span></span> 
    
- <span data-ttu-id="d794a-153">Personalizaciones sin límite.</span><span class="sxs-lookup"><span data-stu-id="d794a-153">Customizations are not limited.</span></span> 
    
#### <a name="on-premises"></a><span data-ttu-id="d794a-154">Implementación local</span><span class="sxs-lookup"><span data-stu-id="d794a-154">On premises</span></span>

<span data-ttu-id="d794a-155">Tiene la propiedad de todo.</span><span class="sxs-lookup"><span data-stu-id="d794a-155">You own everything.</span></span> 
  
<span data-ttu-id="d794a-156">En el diagrama adjunto se muestra un entorno local con servidores web, servidores de aplicaciones y Active Directory, que se comunica con todas las bases de datos y los servidores de aplicaciones dedicados para la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="d794a-156">The accompanying diagram shows an on-premises environment with web servers, application servers, and Active Directory communicating with all databases and dedicated application servers for search.</span></span> 
  
<span data-ttu-id="d794a-157">Entre las características se incluyen: </span><span class="sxs-lookup"><span data-stu-id="d794a-157">Features include:</span></span> 
  
- <span data-ttu-id="d794a-158">Planeamiento de la capacidad y ajuste del tamaño.</span><span class="sxs-lookup"><span data-stu-id="d794a-158">Capacity planning and sizing.</span></span> 
    
- <span data-ttu-id="d794a-159">Adquisición y configuración de servidores.</span><span class="sxs-lookup"><span data-stu-id="d794a-159">Server acquisition and setup.</span></span> 
    
- <span data-ttu-id="d794a-160">Implementación.</span><span class="sxs-lookup"><span data-stu-id="d794a-160">Deployment.</span></span> 
    
- <span data-ttu-id="d794a-161">Escalado horizontal, revisiones y operaciones.</span><span class="sxs-lookup"><span data-stu-id="d794a-161">Scaling out, patching, and operations.</span></span> 
    
- <span data-ttu-id="d794a-162">Copias de seguridad de datos.</span><span class="sxs-lookup"><span data-stu-id="d794a-162">Backing up data.</span></span> 
    
- <span data-ttu-id="d794a-163">Mantenimiento de un entorno de recuperación ante desastres.</span><span class="sxs-lookup"><span data-stu-id="d794a-163">Maintaining a disaster recovery environment.</span></span> 
    
- <span data-ttu-id="d794a-164">Personalizaciones sin límite.</span><span class="sxs-lookup"><span data-stu-id="d794a-164">Customizations are not limited.</span></span> 
    
### <a name="deployment-type-is-best-for---"></a><span data-ttu-id="d794a-p102">Tipo de implementación idóneo para...</span><span class="sxs-lookup"><span data-stu-id="d794a-p102">Deployment type is best for . . .</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="d794a-168">SharePoint 2013 en Office 365</span><span class="sxs-lookup"><span data-stu-id="d794a-168">SharePoint 2013 in Office 365</span></span>

- <span data-ttu-id="d794a-p103">Colaboración y uso compartido con el exterior de forma segura (característica única).</span><span class="sxs-lookup"><span data-stu-id="d794a-p103">Secure external sharing and collaboration. (Unique feature!)</span></span> 
    
- <span data-ttu-id="d794a-171">Intranet: sitios de equipo, Mis sitios y colaboración interna.</span><span class="sxs-lookup"><span data-stu-id="d794a-171">Intranet — Team sites, My Sites, and internal collaboration.</span></span> 
    
- <span data-ttu-id="d794a-172">Almacenamiento de documentos y control de versiones en la nube.</span><span class="sxs-lookup"><span data-stu-id="d794a-172">Document storage and versioning in the cloud.</span></span> 
    
- <span data-ttu-id="d794a-173">Sitio web básico de orientación pública.</span><span class="sxs-lookup"><span data-stu-id="d794a-173">Basic public-facing website.</span></span> 
    
<span data-ttu-id="d794a-174">Características adicionales con los planes de suscripción dedicada de Office 365:</span><span class="sxs-lookup"><span data-stu-id="d794a-174">Additional features with Office 365 Dedicated subscription plans:</span></span> 
  
- <span data-ttu-id="d794a-175">Equipo de centro de datos de Microsoft dedicado a su organización, que no se comparte con ninguna otra.</span><span class="sxs-lookup"><span data-stu-id="d794a-175">Microsoft datacenter equipment that is dedicated to your organization and not shared with any other organization.</span></span> 
    
- <span data-ttu-id="d794a-176">El entorno de cada cliente reside en una red físicamente separada.</span><span class="sxs-lookup"><span data-stu-id="d794a-176">Each customer environment resides in a physically separate network.</span></span> 
    
- <span data-ttu-id="d794a-p104">Comunicación con el cliente mediante una red VPN con protección IPSec o una conexión privada propiedad del cliente. Autenticación en dos fases opcional.</span><span class="sxs-lookup"><span data-stu-id="d794a-p104">Client communication across an IPSec-secured VPN or customer-owned private connection. Two-factor authentication is optional.</span></span> 
    
- <span data-ttu-id="d794a-179">Planes de compatibilidad con ITAR.</span><span class="sxs-lookup"><span data-stu-id="d794a-179">ITAR-support plans.</span></span> 
    
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="d794a-180">Implementación híbrida con Office 365</span><span class="sxs-lookup"><span data-stu-id="d794a-180">Hybrid with Office 365</span></span>

- <span data-ttu-id="d794a-181">Use Office 365 para colaboración y uso compartido con el exterior, en lugar de establecer un entorno de extranet.</span><span class="sxs-lookup"><span data-stu-id="d794a-181">Use Office 365 for external sharing and collaboration instead of setting up an extranet environment.</span></span> 
    
- <span data-ttu-id="d794a-182">Mueva Mis sitios (OneDrive para la Empresa) a la nube para facilitar a los usuarios el acceso a sus archivos de forma remota.</span><span class="sxs-lookup"><span data-stu-id="d794a-182">Move My Sites (OneDrive for Business) to the cloud to make it easier for users to access their files remotely.</span></span> 
    
- <span data-ttu-id="d794a-183">Inicie nuevos sitios de grupo en Office 365.</span><span class="sxs-lookup"><span data-stu-id="d794a-183">Start new team sites in Office 365.</span></span> 
    
- <span data-ttu-id="d794a-184">Integre un sitio de Office 365 con el entorno de BCS de SharePoint local.</span><span class="sxs-lookup"><span data-stu-id="d794a-184">Integrate an Office 365 site with on-premises BCS SharePoint environment.</span></span> 
    
#### <a name="azure"></a><span data-ttu-id="d794a-185">Azure</span><span class="sxs-lookup"><span data-stu-id="d794a-185">Azure</span></span>

- <span data-ttu-id="d794a-p105">SharePoint para Internet Sites: sitios de orientación pública. Aproveche Azure AD para cuentas de cliente y autenticación.</span><span class="sxs-lookup"><span data-stu-id="d794a-p105">SharePoint for Internet Sites — Public facing sites. Take advantage of Azure AD for customer accounts and authentication.</span></span> 
    
- <span data-ttu-id="d794a-188">Entornos de desarrollo, pruebas y almacenamiento provisional: aprovisionar y desaprovisionar entornos completos rápidamente.</span><span class="sxs-lookup"><span data-stu-id="d794a-188">Developer, test, and staging environments — Quickly provision and deprovision entire environments.</span></span> 
    
- <span data-ttu-id="d794a-189">Aplicaciones híbridas: aplicaciones presentes en el centro de datos y la nube.</span><span class="sxs-lookup"><span data-stu-id="d794a-189">Hybrid applications — Applications that span your datacenter and the cloud.</span></span> 
    
- <span data-ttu-id="d794a-p106">Entorno de recuperación ante desastres: disfrutar de recuperación rápida en caso de desastre. Pague solo según uso.</span><span class="sxs-lookup"><span data-stu-id="d794a-p106">Disaster recovery environment — Quickly recover from a disaster. Pay only for use.</span></span> 
    
- <span data-ttu-id="d794a-192">Granjas que requieren auditorías o informes detallados.</span><span class="sxs-lookup"><span data-stu-id="d794a-192">Farms that require deep reporting or auditing.</span></span> 
    
- <span data-ttu-id="d794a-193">Análisis web.</span><span class="sxs-lookup"><span data-stu-id="d794a-193">Web analytics.</span></span> 
    
- <span data-ttu-id="d794a-194">Cifrado de datos en reposo (los datos se cifran en las bases de datos SQL).</span><span class="sxs-lookup"><span data-stu-id="d794a-194">Data encryption at rest (data is encrypted in the SQL databases).</span></span> 
    
#### <a name="data-encryption-at-rest-data-is-encrypted-in-the-sql-databases"></a><span data-ttu-id="d794a-195">Cifrado de datos en reposo (los datos se cifran en las bases de datos SQL)</span><span class="sxs-lookup"><span data-stu-id="d794a-195">Data encryption at rest (data is encrypted in the SQL databases)</span></span>

- <span data-ttu-id="d794a-196">Granjas en territorio nacional (cuando los datos deben encontrarse en el marco geográfico de una jurisdicción).</span><span class="sxs-lookup"><span data-stu-id="d794a-196">In-country farms (when data is required to reside within a jurisdiction).</span></span> 
    
- <span data-ttu-id="d794a-197">Soluciones de BI complejas que deben residir cerca de los datos de BI.</span><span class="sxs-lookup"><span data-stu-id="d794a-197">Complex BI solutions that must reside close to BI data.</span></span> 
    
- <span data-ttu-id="d794a-198">Soluciones de nube privada.</span><span class="sxs-lookup"><span data-stu-id="d794a-198">Private cloud solutions.</span></span> 
    
- <span data-ttu-id="d794a-199">Soluciones muy personalizadas.</span><span class="sxs-lookup"><span data-stu-id="d794a-199">Highly customized solutions.</span></span> 
    
- <span data-ttu-id="d794a-200">Soluciones heredadas con componentes de terceros que dependen de hardware y software que no son compatibles con Servicios de infraestructura de Azure.</span><span class="sxs-lookup"><span data-stu-id="d794a-200">Legacy solutions with third-party components that depend on hardware and software that are not supported on Azure Infrastructure Services.</span></span> 
    
- <span data-ttu-id="d794a-201">Restricciones de privacidad que impiden la sincronización de cuentas de Active Directory con Azure Active Directory (un requisito para Office 365).</span><span class="sxs-lookup"><span data-stu-id="d794a-201">Privacy restrictions that prevent synchronization of Active Directory accounts with Azure Active Directory (a requirement for Office 365).</span></span> 
    
- <span data-ttu-id="d794a-202">Ideal para organizaciones que prefieren tener el control completo de la plataforma y la solución.</span><span class="sxs-lookup"><span data-stu-id="d794a-202">Organizations that prefer control of the entire platform and solution.</span></span> 
    
### <a name="license-requirements"></a><span data-ttu-id="d794a-203">Requisitos de licencia</span><span class="sxs-lookup"><span data-stu-id="d794a-203">License requirements</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="d794a-204">SharePoint 2013 en Office 365</span><span class="sxs-lookup"><span data-stu-id="d794a-204">SharePoint 2013 in Office 365</span></span>

<span data-ttu-id="d794a-p107">Modelo de suscripción. No se requieren licencias adicionales.</span><span class="sxs-lookup"><span data-stu-id="d794a-p107">Subscription model. No additional licenses needed.</span></span> 
  
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="d794a-207">Implementación híbrida con Office 365</span><span class="sxs-lookup"><span data-stu-id="d794a-207">Hybrid with Office 365</span></span>

- <span data-ttu-id="d794a-p108">Office 365: modelo de suscripción. No se requieren licencias adicionales.</span><span class="sxs-lookup"><span data-stu-id="d794a-p108">Office 365 — Subscription model. No additional licenses needed.</span></span> 
    
- <span data-ttu-id="d794a-210">Implementación local: se aplican todas las licencias locales.</span><span class="sxs-lookup"><span data-stu-id="d794a-210">On-premises — All on-premises licenses apply.</span></span> 
    
#### <a name="azure"></a><span data-ttu-id="d794a-211">Azure</span><span class="sxs-lookup"><span data-stu-id="d794a-211">Azure</span></span>

-  <span data-ttu-id="d794a-212">Suscripción de Azure (incluye el sistema operativo del servidor)</span><span class="sxs-lookup"><span data-stu-id="d794a-212">Azure subscription (includes the server operating system)</span></span>
    
- <span data-ttu-id="d794a-213">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d794a-213">SQL Server</span></span> 
    
- <span data-ttu-id="d794a-214">Licencia de servidor de SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="d794a-214">SharePoint 2013 Server License</span></span> 
    
- <span data-ttu-id="d794a-215">Licencia de acceso de cliente de SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="d794a-215">SharePoint 2013 Client Access License</span></span> 
    
#### <a name="on-premises"></a><span data-ttu-id="d794a-216">Implementación local</span><span class="sxs-lookup"><span data-stu-id="d794a-216">On premises</span></span>

- <span data-ttu-id="d794a-217">Sistema operativo del servidor</span><span class="sxs-lookup"><span data-stu-id="d794a-217">Server operating system</span></span> 
    
- <span data-ttu-id="d794a-218">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d794a-218">SQL Server</span></span> 
    
- <span data-ttu-id="d794a-219">Licencia de servidor de SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="d794a-219">SharePoint 2013 Server License</span></span> 
    
- <span data-ttu-id="d794a-220">Licencia de acceso de cliente de SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="d794a-220">SharePoint 2013 Client Access License</span></span> 
    
### <a name="architecture-tasks"></a><span data-ttu-id="d794a-221">Tareas de arquitectura</span><span class="sxs-lookup"><span data-stu-id="d794a-221">Architecture tasks</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="d794a-222">SharePoint 2013 en Office 365</span><span class="sxs-lookup"><span data-stu-id="d794a-222">SharePoint 2013 in Office 365</span></span>

- <span data-ttu-id="d794a-p109">Planee y diseñe la integración de directorios. Dos opciones. Cualquier de las dos opciones se puede implementar de forma local o en Azure: Sincronización de contraseñas (requiere un servidor de 64 bits). SSO (requiere AD FS y varios servidores).</span><span class="sxs-lookup"><span data-stu-id="d794a-p109">Plan and design directory integration. Two options. Either option can be deployed on premises or in Azure: Password sync (requires one 64-bit server). SSO (requires AD FS and multiple servers).</span></span> 
    
- <span data-ttu-id="d794a-227">Garantice la capacidad de la red y la disponibilidad a través de firewalls, servidores proxy, puertas de enlace y vínculos WAN.</span><span class="sxs-lookup"><span data-stu-id="d794a-227">Ensure network capacity and availability through firewalls, proxy servers, gateways, and across WAN links.</span></span> 
    
- <span data-ttu-id="d794a-228">Adquirir certificados SSL de terceros para proporcionar seguridad empresarial para las ofertas de servicio de Office 365.</span><span class="sxs-lookup"><span data-stu-id="d794a-228">Acquire third-party SSL certificates to provide enterprise-security for Office 365 service offerings.</span></span> 
    
- <span data-ttu-id="d794a-229">Planee el nombre del inquilino y diseñe el gobierno y la arquitectura de la colección de sitios.</span><span class="sxs-lookup"><span data-stu-id="d794a-229">Plan the tenant name, and design the site collection architecture and governance.</span></span> 
    
- <span data-ttu-id="d794a-230">Planee personalizaciones, soluciones y aplicaciones para SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="d794a-230">Plan customizations, solutions, and apps for SharePoint Online.</span></span> 
    
- <span data-ttu-id="d794a-p110">Decida si desea conectarse a Office 365 usando el protocolo de Internet 6 (IPv6). Esta opción es poco frecuente.</span><span class="sxs-lookup"><span data-stu-id="d794a-p110">Decide if you want to connect to Office 365 by using the Internet Protocol 6 (IPv6). This is not common.</span></span> 
    
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="d794a-233">Implementación híbrida con Office 365</span><span class="sxs-lookup"><span data-stu-id="d794a-233">Hybrid with Office 365</span></span>

<span data-ttu-id="d794a-234">Además de las tareas para entornos Office 365 y locales:</span><span class="sxs-lookup"><span data-stu-id="d794a-234">In addition to tasks for both the Office 365 and on-premises environments:</span></span> 
  
- <span data-ttu-id="d794a-p111">Determine qué nivel de integración de características desea y elija la topología híbrida. Vea este póster modelo: ¿Qué topología híbrida debo usar?</span><span class="sxs-lookup"><span data-stu-id="d794a-p111">Determine how much feature integration you want and choose the hybrid topology. See this model poster: Which hybrid topology should I use?</span></span> 
    
- <span data-ttu-id="d794a-237">Si es necesario, determine qué dispositivo servidor proxy se usará.</span><span class="sxs-lookup"><span data-stu-id="d794a-237">If required, determine which proxy server device will be used.</span></span> 
    
#### <a name="azure"></a><span data-ttu-id="d794a-238">Azure</span><span class="sxs-lookup"><span data-stu-id="d794a-238">Azure</span></span>

<span data-ttu-id="d794a-239">Diseñar el entorno de red de Azure:</span><span class="sxs-lookup"><span data-stu-id="d794a-239">Design the Azure network environment:</span></span> 
  
- <span data-ttu-id="d794a-240">Red virtual en Azure, incluidas las subredes.</span><span class="sxs-lookup"><span data-stu-id="d794a-240">Virtual network within Azure, including subnets.</span></span> 
    
- <span data-ttu-id="d794a-241">Entorno de dominio e integración con servidores locales.</span><span class="sxs-lookup"><span data-stu-id="d794a-241">Domain environment and integration with on-premises servers.</span></span> 
    
- <span data-ttu-id="d794a-242">Direcciones IP y DNS.</span><span class="sxs-lookup"><span data-stu-id="d794a-242">IP addresses and DNS.</span></span> 
    
- <span data-ttu-id="d794a-243">Grupos de afinidad y cuentas de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="d794a-243">Affinity groups and storage accounts.</span></span> 
    
<span data-ttu-id="d794a-244">Diseñar el entorno de SharePoint en Azure:</span><span class="sxs-lookup"><span data-stu-id="d794a-244">Design the SharePoint environment in Azure:</span></span> 
  
- <span data-ttu-id="d794a-245">Topología de granja de SharePoint y arquitectura lógica.</span><span class="sxs-lookup"><span data-stu-id="d794a-245">SharePoint farm topology and logical architecture.</span></span> 
    
-  <span data-ttu-id="d794a-246">Conjuntos de disponibilidad de Azure y dominios de actualización.</span><span class="sxs-lookup"><span data-stu-id="d794a-246">Azure availability sets and update domains.</span></span>
    
- <span data-ttu-id="d794a-247">Tamaños de máquinas virtuales.</span><span class="sxs-lookup"><span data-stu-id="d794a-247">Virtual machines sizes.</span></span> 
    
- <span data-ttu-id="d794a-248">Extremo con equilibrio de carga.</span><span class="sxs-lookup"><span data-stu-id="d794a-248">Load balanced endpoint.</span></span> 
    
- <span data-ttu-id="d794a-249">Extremos externos para acceso público, si se prefiere así.</span><span class="sxs-lookup"><span data-stu-id="d794a-249">External endpoints for public access, if that is preferable.</span></span> 
    
- <span data-ttu-id="d794a-250">Entorno de recuperación ante desastres.</span><span class="sxs-lookup"><span data-stu-id="d794a-250">Disaster recovery environment.</span></span> 
    
#### <a name="on-premises"></a><span data-ttu-id="d794a-251">Implementación local</span><span class="sxs-lookup"><span data-stu-id="d794a-251">On premises</span></span>

<span data-ttu-id="d794a-252">Diseñar el entorno de SharePoint en un entorno local existente:</span><span class="sxs-lookup"><span data-stu-id="d794a-252">Design the SharePoint environment in an existing on-premises environment:</span></span> 
  
- <span data-ttu-id="d794a-253">Topología de granja de SharePoint y arquitectura lógica. </span><span class="sxs-lookup"><span data-stu-id="d794a-253">SharePoint farm topology and logical architecture.</span></span> 
    
- <span data-ttu-id="d794a-254">Hardware de servidores.</span><span class="sxs-lookup"><span data-stu-id="d794a-254">Server hardware.</span></span> 
    
- <span data-ttu-id="d794a-255">Entorno virtual, si se usa.</span><span class="sxs-lookup"><span data-stu-id="d794a-255">Virtual environment, if used.</span></span> 
    
- <span data-ttu-id="d794a-256">Equilibrio de carga.</span><span class="sxs-lookup"><span data-stu-id="d794a-256">Load balancing.</span></span> 
    
- <span data-ttu-id="d794a-257">Integración con AD DS y DNS.</span><span class="sxs-lookup"><span data-stu-id="d794a-257">Integration with AD DS and DNS.</span></span> 
    
- <span data-ttu-id="d794a-258">Entorno de recuperación ante desastres.</span><span class="sxs-lookup"><span data-stu-id="d794a-258">Disaster recovery environment.</span></span> 
    
### <a name="it-pro-responsibilities"></a><span data-ttu-id="d794a-259">Responsabilidades del profesional de TI</span><span class="sxs-lookup"><span data-stu-id="d794a-259">IT pro responsibilities</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="d794a-260">SharePoint 2013 en Office 365</span><span class="sxs-lookup"><span data-stu-id="d794a-260">SharePoint 2013 in Office 365</span></span>

- <span data-ttu-id="d794a-261">Asegurarse de que las estaciones de trabajo de los usuarios cumplen los requisitos previos de cliente de Office 365.</span><span class="sxs-lookup"><span data-stu-id="d794a-261">Ensure user workstations meet Office 365 client prerequisites.</span></span> 
    
- <span data-ttu-id="d794a-262">Implementar el plan de integración de directorios.</span><span class="sxs-lookup"><span data-stu-id="d794a-262">Implement the directory integration plan.</span></span> 
    
- <span data-ttu-id="d794a-263">Planee e implemente enrutamiento y registros DNS internos y externos.</span><span class="sxs-lookup"><span data-stu-id="d794a-263">Plan and implement internal and external DNS records and routing.</span></span> 
    
- <span data-ttu-id="d794a-264">Configurar el proxy o el servidor de seguridad conforme a los requisitos de dirección IP y URL de Office 365.</span><span class="sxs-lookup"><span data-stu-id="d794a-264">Configure the proxy or firewall for Office 365 IP address and URL requirements.</span></span> 
    
- <span data-ttu-id="d794a-265">Cree y asigne permisos a colecciones de sitios.</span><span class="sxs-lookup"><span data-stu-id="d794a-265">Create and assign permissions to site collections.</span></span> 
    
- <span data-ttu-id="d794a-266">Implemente personalizaciones, soluciones y aplicaciones para SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="d794a-266">Implement customizations, solutions, and apps for SharePoint Online.</span></span> 
    
- <span data-ttu-id="d794a-267">Supervise la disponibilidad de red e identifique posibles cuellos de botella.</span><span class="sxs-lookup"><span data-stu-id="d794a-267">Monitor network availability and identify possible bottlenecks.</span></span> 
    
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="d794a-268">Implementación híbrida con Office 365</span><span class="sxs-lookup"><span data-stu-id="d794a-268">Hybrid with Office 365</span></span>

<span data-ttu-id="d794a-269">Además de las tareas para entornos Office 365 y locales:</span><span class="sxs-lookup"><span data-stu-id="d794a-269">In addition to tasks for both the Office 365 and on-premises environments:</span></span> 
  
- <span data-ttu-id="d794a-270">Configure el servidor proxy, si es necesario.</span><span class="sxs-lookup"><span data-stu-id="d794a-270">Configure the proxy server device, if required.</span></span> 
    
- <span data-ttu-id="d794a-271">Configure la infraestructura híbrida de administración de identidades: SSO y autenticación de servidor a servidor entre los dos entornos.</span><span class="sxs-lookup"><span data-stu-id="d794a-271">Configure the hybrid identity management infrastructure: SSO and server-to-server authentication between the two environments.</span></span> 
    
- <span data-ttu-id="d794a-272">Configurar la integración de las características elegidas: búsqueda, BCS, Duet Enterprise Online.</span><span class="sxs-lookup"><span data-stu-id="d794a-272">Configure the integration of chosen features: Search, BCS, Duet Enterprise Online.</span></span> 
    
#### <a name="azure"></a><span data-ttu-id="d794a-273">Azure</span><span class="sxs-lookup"><span data-stu-id="d794a-273">Azure</span></span>

<span data-ttu-id="d794a-274">Implementar y administrar el entorno de Azure y SharePoint:</span><span class="sxs-lookup"><span data-stu-id="d794a-274">Deploy and manage the Azure and SharePoint environment:</span></span> 
  
- <span data-ttu-id="d794a-275">Implemente y administre el entorno de red de Azure.</span><span class="sxs-lookup"><span data-stu-id="d794a-275">Implement and manage the Azure network environment.</span></span> 
    
- <span data-ttu-id="d794a-276">Implemente el entorno de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="d794a-276">Deploy the SharePoint environment.</span></span> 
    
- <span data-ttu-id="d794a-277">Actualice los servidores de la granja de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="d794a-277">Update SharePoint farm servers.</span></span> 
    
- <span data-ttu-id="d794a-278">Agregue o desconecte máquinas virtuales según sea necesario en función del uso de la granja.</span><span class="sxs-lookup"><span data-stu-id="d794a-278">Add or shut down virtual machines as needed based on farm utilization.</span></span> 
    
- <span data-ttu-id="d794a-279">Aumente o reduzca el tamaño de las máquinas virtuales, en función de las necesidades.</span><span class="sxs-lookup"><span data-stu-id="d794a-279">Increase or decrease virtual machine sizes, as needed.</span></span> 
    
- <span data-ttu-id="d794a-280">Haga copia de seguridad del entorno de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="d794a-280">Back up the SharePoint environment.</span></span> 
    
- <span data-ttu-id="d794a-281">Implemente el entorno de recuperación ante desastres y el protocolo. </span><span class="sxs-lookup"><span data-stu-id="d794a-281">Implement the disaster recovery environment and protocol.</span></span> 
    
#### <a name="on-premises"></a><span data-ttu-id="d794a-282">Implementación local</span><span class="sxs-lookup"><span data-stu-id="d794a-282">On premises</span></span>

<span data-ttu-id="d794a-283">Implementar y administrar el entorno SharePoint local:</span><span class="sxs-lookup"><span data-stu-id="d794a-283">Deploy and manage the SharePoint on premises environment:</span></span> 
  
- <span data-ttu-id="d794a-284">Aprovisionar servidores.</span><span class="sxs-lookup"><span data-stu-id="d794a-284">Provision servers.</span></span> 
    
- <span data-ttu-id="d794a-285">Implementar el entorno SharePoint.</span><span class="sxs-lookup"><span data-stu-id="d794a-285">Deploy the SharePoint environment.</span></span> 
    
- <span data-ttu-id="d794a-286">Actualice los servidores de la granja de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="d794a-286">Update SharePoint farm servers.</span></span> 
    
- <span data-ttu-id="d794a-287">Agregue o quite servidores de la granja según sea necesario en función del uso de la granja de servidores.</span><span class="sxs-lookup"><span data-stu-id="d794a-287">Add or remove farm servers as needed based on farm utilization.</span></span> 
    
- <span data-ttu-id="d794a-288">Haga copia de seguridad del entorno de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="d794a-288">Back up the SharePoint environment.</span></span> 
    
- <span data-ttu-id="d794a-289">Implemente el entorno de recuperación ante desastres y el protocolo.</span><span class="sxs-lookup"><span data-stu-id="d794a-289">Implement the disaster recovery environment and protocol.</span></span> 
    
## <a name="three-typical-workloads-to-move-to-azure"></a><span data-ttu-id="d794a-290">Tres cargas de trabajo típicas para pasar a Azure</span><span class="sxs-lookup"><span data-stu-id="d794a-290">Three typical workloads to move to Azure</span></span>

### <a name="office-365-plus-directory-components-in-azure"></a><span data-ttu-id="d794a-291">Office 365 y componentes de directorio de Azure</span><span class="sxs-lookup"><span data-stu-id="d794a-291">Office 365 plus Directory Components in Azure</span></span>

<span data-ttu-id="d794a-292">Implementar los componentes de integración de directorios de Office 365 en Azure es más rápido porque permite implementar máquinas virtuales a petición.</span><span class="sxs-lookup"><span data-stu-id="d794a-292">Deploying Office 365 directory integration components in Azure is faster because it can deploy virtual machines on-demand.</span></span> 
  
#### <a name="directory-synchronization-server-only"></a><span data-ttu-id="d794a-293">Solo servidor de sincronización de directorios</span><span class="sxs-lookup"><span data-stu-id="d794a-293">Directory synchronization server only</span></span>

<span data-ttu-id="d794a-294">En lugar de implementar el servidor de sincronización de directorios de 64 bits en el entorno local, se aprovisiona una máquina virtual en Azure.</span><span class="sxs-lookup"><span data-stu-id="d794a-294">Instead of deploying the 64-bit directory synchronization server in your on-premises environment, provision a virtual machine in Azure instead.</span></span> 
  
<span data-ttu-id="d794a-295">En el diagrama adjunto se muestra SharePoint Online con un inquilino de Azure Active Directory que sincroniza nombres de cuentas y contraseñas entre el entorno local de Active Directory y el inquilino de Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="d794a-295">The accompanying diagram shows SharePoint Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span> 
  
#### <a name="directory-synchronization-plus-ad-fs"></a><span data-ttu-id="d794a-296">Sincronización de directorios + AD FS</span><span class="sxs-lookup"><span data-stu-id="d794a-296">Directory synchronization plus AD FS</span></span>

<span data-ttu-id="d794a-p112">Gracias a esta opción, se admiten las identidades federadas de Office 365 sin necesidad de agregar hardware a la infraestructura local. También ofrece resistencia si el entorno de Active Directory local no está disponible.</span><span class="sxs-lookup"><span data-stu-id="d794a-p112">This option allows you to support Office 365 federated identities (SSO) without adding hardware to your on-premises infrastructure. It also provides resiliency if the on-premises Active Directory environment is unavailable.</span></span> 
  
- <span data-ttu-id="d794a-299">Los componentes de integración de directorios residen en Azure.</span><span class="sxs-lookup"><span data-stu-id="d794a-299">Directory integration components reside in Azure.</span></span> 
    
- <span data-ttu-id="d794a-300">AD FS se publica en Internet a través de servidores proxy de AD FS en Azure.</span><span class="sxs-lookup"><span data-stu-id="d794a-300">AD FS is published to the Internet through AD FS proxies in Azure.</span></span> 
    
- <span data-ttu-id="d794a-301">En el caso de usuarios que se conectan desde cualquier ubicación, el tráfico de autenticación de cliente se controla a través de servidores de AD FS y servidores proxy que se encuentran implementados en Azure.</span><span class="sxs-lookup"><span data-stu-id="d794a-301">Client authentication traffic, for users that are connecting from any location, is handled by AD FS servers and proxies that are deployed on Azure.</span></span> 
    
### <a name="public-facing-internet-site-and-azure-ad-for-customer-authentication"></a><span data-ttu-id="d794a-302">Sitio de Internet de orientación pública y Azure AD para autenticación de clientes</span><span class="sxs-lookup"><span data-stu-id="d794a-302">Public-facing Internet site and Azure AD for customer authentication</span></span>

<span data-ttu-id="d794a-p113">Traiga su sitio de Internet a Azure y disfrute de la posibilidad de escalar recursos fácilmente según sus necesidades. Use Azure AD para almacenar cuentas de clientes.</span><span class="sxs-lookup"><span data-stu-id="d794a-p113">Take advantage of the ability to easily scale to demand by placing your Internet site in Azure. Use Azure AD to store customer accounts.</span></span> 
  
#### <a name="azure-advantages-for-internet-sites"></a><span data-ttu-id="d794a-305">Ventajas de Azure para sitios de Internet</span><span class="sxs-lookup"><span data-stu-id="d794a-305">Azure advantages for Internet sites</span></span>

- <span data-ttu-id="d794a-306">Pague solo por los recursos que necesite ampliando el número de máquinas virtuales en función del uso de la granja de servidores.</span><span class="sxs-lookup"><span data-stu-id="d794a-306">Pay only for the resources you need by scaling the number of virtual machines based on farm utilization.</span></span> 
    
- <span data-ttu-id="d794a-307">Agregue informes detallados y análisis web.</span><span class="sxs-lookup"><span data-stu-id="d794a-307">Add deep reporting and web analytics.</span></span> 
    
- <span data-ttu-id="d794a-308">Céntrese en desarrollar un sitio impresionante en lugar de tener que crear una infraestructura.</span><span class="sxs-lookup"><span data-stu-id="d794a-308">Focus on developing a great site rather than building infrastructure.</span></span> 
    
#### <a name="azure-ad"></a><span data-ttu-id="d794a-309">Azure AD</span><span class="sxs-lookup"><span data-stu-id="d794a-309">Azure AD</span></span>

<span data-ttu-id="d794a-p114">Azure AD proporciona capacidades de control de acceso y administración de identidades para servicios en la nube. Entre las capacidades se incluye un almacén basado en la nube para los datos del directorio y un conjunto esencial de servicios de identidad (que incluye procesos de inicio de sesión del usuario, servicios de autenticación y AD FS). Los servicios de identidad que se incluyen con Azure AD se integran fácilmente en las implementaciones locales de Active Directory y son totalmente compatibles con los proveedores de identidades de terceros.</span><span class="sxs-lookup"><span data-stu-id="d794a-p114">Azure AD provides identity management and access control capabilities for cloud services. Capabilities include a cloud-based store for directory data and a core set of identity services, including user logon processes, authentication services, and AD FS. The identity services that are included with Azure AD easily integrate with your on-premises Active Directory deployments and fully support third-party identity providers.</span></span> 
  
<span data-ttu-id="d794a-p115">En el diagrama adjunto se muestra la configuración de las zonas y la autenticación que son importantes para los sitios orientados a Internet. En el diagrama se muestra el inquilino de Azure Active Directory, que contiene una granja de SharePoint en Azure con dos zonas:</span><span class="sxs-lookup"><span data-stu-id="d794a-p115">The accompanying diagram shows the configuration of zones and authentication that is important for Internet-facing sites. The diagram shows the Azure Active Directory Tenant, which contains a SharePoint Farm on Azure with two zones:</span></span> 
  
- <span data-ttu-id="d794a-315">Una zona de Internet que interactúa con los visitantes anónimos y autenticados y clientes fuera de la red.</span><span class="sxs-lookup"><span data-stu-id="d794a-315">An Internet zone that interacts with Anonymous and Authenticated visitors and customers outside the network</span></span> 
    
- <span data-ttu-id="d794a-316">Una zona predeterminada que contiene NTLM para rastreo y la autenticación de Windows que interactúa con la implementación local de Active Directory a través de un túnel VPN.</span><span class="sxs-lookup"><span data-stu-id="d794a-316">A default zone that contains NTLM for Crawl and Windows Authentication that interacts with your on-premises Active Directory deployment over a VPN tunnel.</span></span> 
    
### <a name="on-premises-farm-plus-disaster-recovery-in-azure"></a><span data-ttu-id="d794a-317">Granja local y recuperación ante desastres en Azure</span><span class="sxs-lookup"><span data-stu-id="d794a-317">On-premises Farm plus Disaster Recovery in Azure</span></span>

<span data-ttu-id="d794a-p116">Elija una opción de recuperación ante desastres que se adapte a los requisitos de su empresa. Azure ofrece opciones básicas para empresas que están comenzando en la recuperación ante desastres, así como opciones avanzadas para empresas que requieren un alto nivel de resistencia.</span><span class="sxs-lookup"><span data-stu-id="d794a-p116">Choose a disaster recovery option that matches your business requirements. Azure provides entry-level options for companies getting started with disaster recovery and advanced options for enterprises with high resiliency requirements.</span></span> 
  
#### <a name="cold-standby"></a><span data-ttu-id="d794a-320">Espera pasiva</span><span class="sxs-lookup"><span data-stu-id="d794a-320">Cold standby</span></span>

- <span data-ttu-id="d794a-p117">La granja de servidores se ha creado por completo, pero las máquinas virtuales están detenidas (solo paga cuando se están ejecutando).</span><span class="sxs-lookup"><span data-stu-id="d794a-p117">The farm is fully built, but the virtual machines are stopped. (You're paying only when they're running!)</span></span> 
    
- <span data-ttu-id="d794a-323">Para realizar el mantenimiento del entorno, hay que iniciar las máquinas virtuales de vez en cuando, revisar, actualizar y comprobar el entorno.</span><span class="sxs-lookup"><span data-stu-id="d794a-323">Maintaining the environment includes starting the virtual machines from time-to-time, patching, updating, and verifying the environment.</span></span> 
    
- <span data-ttu-id="d794a-324">En caso de desastre, inicie el entorno completo.</span><span class="sxs-lookup"><span data-stu-id="d794a-324">Start the full environment in the event of a disaster.</span></span> 
    
#### <a name="warm-standby"></a><span data-ttu-id="d794a-325">Espera semiactiva</span><span class="sxs-lookup"><span data-stu-id="d794a-325">Warm standby</span></span>

- <span data-ttu-id="d794a-326">Incluye una pequeña granja aprovisionada y en funcionamiento.</span><span class="sxs-lookup"><span data-stu-id="d794a-326">This includes a small farm that is provisioned and running.</span></span> 
    
- <span data-ttu-id="d794a-327">La granja puede atender a los usuarios inmediatamente en caso de conmutación por error.</span><span class="sxs-lookup"><span data-stu-id="d794a-327">The farm can immediately serve users in the event of a failover.</span></span> 
    
- <span data-ttu-id="d794a-328">Puede ampliar la granja con rapidez para dar servicio a toda la base de usuarios.</span><span class="sxs-lookup"><span data-stu-id="d794a-328">Scale out the farm quickly to serve the full user base.</span></span> 
    
#### <a name="hot-standby"></a><span data-ttu-id="d794a-329">Espera activa</span><span class="sxs-lookup"><span data-stu-id="d794a-329">Hot standby</span></span>

<span data-ttu-id="d794a-330">Se aprovisiona y ejecuta una granja completa en modo de espera.</span><span class="sxs-lookup"><span data-stu-id="d794a-330">A fully-sized farm is provisioned and running on standby.</span></span> 
  
<span data-ttu-id="d794a-p118">En el diagrama adjunto se muestra una granja local que interactúa con el entorno de recuperación ante desastres de SharePoint en Azure. Las bases de datos locales usan el trasvase de registros de SQL Server a través del túnel VPN para acceder al entorno de recuperación ante desastres de SharePoint, que incluye dos servidores de Base de datos SQL que contienen las bases de datos de SharePoint, dos servidores front-end web y dos servidores de aplicaciones de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="d794a-p118">The accompanying diagram shows an on-premises farm interacting with the SharePoint Disaster Recovery Environment on Azure. The on-premises databases use SQL Server Log Shipping over the VPN tunnel to access the SharePoint Disaster Recovery environment, which includes two SQL database servers that contain the SharePoint databases, two Web Front End servers, and two SharePoint Application servers.</span></span> 
  

