---
title: Diagrama accesible Opciones de plataformas de Microsoft Lync 2013
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 2858d1e7-be37-4484-b121-a99779742a38
description: Este artículo es una versión de texto accesible del diagrama con el nombre Opciones de plataformas de Microsoft Lync 2013, que está disponible en Diagramas técnicos.
ms.openlocfilehash: 4993ad90307973589da6dc5081d8c2875b44ce66
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068616"
---
# <a name="accessible-diagram---microsoft-lync-2013-platform-options"></a><span data-ttu-id="a5f16-103">Diagrama accesible: Opciones de plataformas de Microsoft Lync 2013</span><span class="sxs-lookup"><span data-stu-id="a5f16-103">Accessible diagram - Microsoft Lync 2013 Platform Options</span></span>

<span data-ttu-id="a5f16-104">**Resumen:** este artículo es una versión de texto accesible del diagrama “Opciones de plataformas de Microsoft Lync 2013”, que está disponible en [Diagramas técnicos](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span><span class="sxs-lookup"><span data-stu-id="a5f16-104">**Summary:** This article is an accessible text version of the diagram named Microsoft Lync 2013 Platform Options, which is available at [Technical Diagrams](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span></span>
  
<span data-ttu-id="a5f16-105">Este póster describe lo que los arquitectos y responsables de decisiones empresariales (BDM) necesitan saber sobre implementaciones de Lync Online (Office 365) y Lync Server. Incluye lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="a5f16-105">This poster describes what business decision makers (BDMs) and architects need to know about Lync Online (Office 365) and Lync Server deployments and includes:</span></span>
  
- <span data-ttu-id="a5f16-106">Una comparación de cuatro diferentes opciones de implementación: Lync Online (Office 365), implementación híbrida de Lync Online/Server, Lync Server y Lync Server hospedado por el proveedor.</span><span class="sxs-lookup"><span data-stu-id="a5f16-106">A comparison of four different deployment options: Lync Online (Office 365), Lync Online/Server Hybrid, Lync Server, and Provider-Hosted Lync Server.</span></span> 
    
- <span data-ttu-id="a5f16-107">Dos escenarios de ejemplo para implementar Lync 2013.</span><span class="sxs-lookup"><span data-stu-id="a5f16-107">Two example scenarios for deploying Lync 2013.</span></span>
    
## <a name="comparison-of-four-different-deployments-for-the-lync-2013-platform"></a><span data-ttu-id="a5f16-108">Comparación de cuatro implementaciones diferentes para la plataforma de Lync 2013</span><span class="sxs-lookup"><span data-stu-id="a5f16-108">Comparison of four different deployments for the Lync 2013 platform</span></span>

<span data-ttu-id="a5f16-109">La comparación proporciona información sobre cada opción de implementación en las siguientes áreas:</span><span class="sxs-lookup"><span data-stu-id="a5f16-109">The comparison provides information about each deployment option in the following areas:</span></span> 
  
- <span data-ttu-id="a5f16-110">Información general sobre las diferentes características de implementación</span><span class="sxs-lookup"><span data-stu-id="a5f16-110">An overview of the different deployment features</span></span>
    
- <span data-ttu-id="a5f16-111">Ventajas de la implementación de cada opción de implementación</span><span class="sxs-lookup"><span data-stu-id="a5f16-111">Benefits of implementing each deployment option</span></span>
    
- <span data-ttu-id="a5f16-112">Requisitos de licencia</span><span class="sxs-lookup"><span data-stu-id="a5f16-112">Licensing requirements</span></span>
    
- <span data-ttu-id="a5f16-113">Tareas de arquitectura requeridas</span><span class="sxs-lookup"><span data-stu-id="a5f16-113">Required architectural tasks</span></span>
    
- <span data-ttu-id="a5f16-114">Responsabilidades del profesional de TI para implementar cada opción de implementación</span><span class="sxs-lookup"><span data-stu-id="a5f16-114">IT Pro responsibilities for implementing each deployment option</span></span>
    
### <a name="overview"></a><span data-ttu-id="a5f16-115">Información general</span><span class="sxs-lookup"><span data-stu-id="a5f16-115">Overview</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="a5f16-116">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="a5f16-116">Lync Online (Office 365)</span></span>

<span data-ttu-id="a5f16-117">Aumente su eficiencia y optimice los costos con los planes multiempresa de Office 365.</span><span class="sxs-lookup"><span data-stu-id="a5f16-117">You gain efficiency and optimize for cost with Office 365 multitenant plans.</span></span>
  
<span data-ttu-id="a5f16-118">El diagrama correspondiente muestra Lync Online con un inquilino de Azure Active Directory que sincroniza nombres y contraseñas de cuentas entre el entorno de Servicios de dominio de Active Directory (AD DS) y el inquilino de Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="a5f16-118">The accompanying diagram shows Lync Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span> 
  
<span data-ttu-id="a5f16-119">Descripción de las características y funcionalidades:</span><span class="sxs-lookup"><span data-stu-id="a5f16-119">Description of features and functionality:</span></span>
  
- <span data-ttu-id="a5f16-120">Software como servicio (SaaS).</span><span class="sxs-lookup"><span data-stu-id="a5f16-120">Software as a Service (SaaS).</span></span>
    
- <span data-ttu-id="a5f16-121">Amplio conjunto de características que siempre está actualizado.</span><span class="sxs-lookup"><span data-stu-id="a5f16-121">Rich feature set that is always up to date.</span></span>
    
- <span data-ttu-id="a5f16-122">Incluye un inquilino de Azure Active Directory para cuentas en línea que se puede usar con otras aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="a5f16-122">Includes an Azure Active Directory tenant for online accounts, which can be used with other applications.</span></span> 
    
- <span data-ttu-id="a5f16-123">La integración de directorios incluye sincronización de nombres y contraseñas de cuentas entre el entorno de Servicios de dominio de Active Directory (AD DS) local y el inquilino de Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="a5f16-123">Directory integration includes synchronizing account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span>
    
- <span data-ttu-id="a5f16-124">Si se requiere inicio de sesión único (SSO), se debe implementar los Servicios de federación de Active Directory (AD FS).</span><span class="sxs-lookup"><span data-stu-id="a5f16-124">If single sign-on (SSO) is a requirement, Active Directory Federation Services (AD FS) must be implemented.</span></span> 
    
- <span data-ttu-id="a5f16-125">La comunicación con el cliente por Internet está cifrada y autenticada.</span><span class="sxs-lookup"><span data-stu-id="a5f16-125">Client communication over the Internet is encrypted and authenticated.</span></span>
    
- <span data-ttu-id="a5f16-126">La conectividad para el equipo telefónico heredado a través de la red telefónica conmutada (RTC) está disponible con proveedores de terceros.</span><span class="sxs-lookup"><span data-stu-id="a5f16-126">Legacy phone equipment, public switched telephone network (PSTN), connectivity is available through third-party providers.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="a5f16-127">Implementación híbrida de Lync Online/Server (dominio dividido)</span><span class="sxs-lookup"><span data-stu-id="a5f16-127">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="a5f16-128">Puede combinar las ventajas de Office 365 con una implementación local de Lync 2013.</span><span class="sxs-lookup"><span data-stu-id="a5f16-128">You can combine the benefits of Office 365 with an on-premises deployment of Lync 2013.</span></span>
  
<span data-ttu-id="a5f16-p101">En el diagrama adjunto se muestra Office 365 con Lync Online, donde algunos usuarios están alojados localmente y otros en línea. También se muestra un servidor perimetral implementado de manera local.</span><span class="sxs-lookup"><span data-stu-id="a5f16-p101">The accompanying diagram shows Office 365 with Lync Online where some users are homed on-premises and some users are homed online. An Edge Server that is deployed on-premises is also shown.</span></span>
  
<span data-ttu-id="a5f16-131">Descripción de las características y funcionalidades:</span><span class="sxs-lookup"><span data-stu-id="a5f16-131">Description of features and functionality:</span></span>
  
- <span data-ttu-id="a5f16-132">Algunos usuarios se alojan de forma local y otros se alojan en línea, pero todos comparten el mismo dominio SIP (por ejemplo, contoso.com).</span><span class="sxs-lookup"><span data-stu-id="a5f16-132">Some users are homed on premises and some users are homed online, but the users share the same SIP domain (such as contoso.com).</span></span>
    
- <span data-ttu-id="a5f16-133">Se aprovecha la infraestructura de Lync Server 2013 existente, incluidas las conexiones a la RTC.</span><span class="sxs-lookup"><span data-stu-id="a5f16-133">Leverage your existing Lync Server 2013 infrastructure, including the connections to the PSTN.</span></span>
    
- <span data-ttu-id="a5f16-134">Agregue nuevos usuarios Lync Online fácilmente cuando no estos no requieran RTC.</span><span class="sxs-lookup"><span data-stu-id="a5f16-134">Add new Lync Online users easily when they do not require PSTN.</span></span>
    
- <span data-ttu-id="a5f16-135">Migre desde Lync local a Lync Online con el transcurso del tiempo, según la programación deseada.</span><span class="sxs-lookup"><span data-stu-id="a5f16-135">Migrate from Lync on-premises to Lync Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="a5f16-136">Se integra con otras aplicaciones de Office 365, incluidas Exchange Online y SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="a5f16-136">Integrate with other Office 365 applications, including Exchange Online and SharePoint Online.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="a5f16-137">Lync Server</span><span class="sxs-lookup"><span data-stu-id="a5f16-137">Lync Server</span></span>

<span data-ttu-id="a5f16-p102">En esta implementación, todo es propiedad suya. El diagrama correspondiente muestra una infraestructura de Lync Server con un entorno de Active Directory Domain Services (AD DS) local donde los usuarios están alojados de forma local.</span><span class="sxs-lookup"><span data-stu-id="a5f16-p102">In this deployment, you own everything. The accompanying diagram shows a Lync Server infrastructure with an on-premises Active Directory Domain Services (AD DS) environment where users are homed on-premises.</span></span>
  
<span data-ttu-id="a5f16-140">Descripción de las características y funcionalidades:</span><span class="sxs-lookup"><span data-stu-id="a5f16-140">Description of features and functionality:</span></span>
  
- <span data-ttu-id="a5f16-141">Planeamiento de la capacidad y ajuste del tamaño.</span><span class="sxs-lookup"><span data-stu-id="a5f16-141">Capacity planning and sizing.</span></span>
    
- <span data-ttu-id="a5f16-142">Adquisición y configuración de servidores.</span><span class="sxs-lookup"><span data-stu-id="a5f16-142">Server acquisition and setup.</span></span>
    
- <span data-ttu-id="a5f16-143">Implementación.</span><span class="sxs-lookup"><span data-stu-id="a5f16-143">Deployment.</span></span>
    
- <span data-ttu-id="a5f16-144">Escalado horizontal, revisiones y operaciones.</span><span class="sxs-lookup"><span data-stu-id="a5f16-144">Scaling out, patching, and operations.</span></span>
    
- <span data-ttu-id="a5f16-145">Copias de seguridad de datos.</span><span class="sxs-lookup"><span data-stu-id="a5f16-145">Backing up data.</span></span>
    
- <span data-ttu-id="a5f16-146">Mantenimiento de conmutación por error y recuperación ante desastres.</span><span class="sxs-lookup"><span data-stu-id="a5f16-146">Maintaining failover and disaster recovery.</span></span>
    
- <span data-ttu-id="a5f16-147">Conexión de la infraestructura de Lync Server 2013 a la RTC.</span><span class="sxs-lookup"><span data-stu-id="a5f16-147">Connecting your Lync Server 2013 infrastructure to the PSTN.</span></span>
    
- <span data-ttu-id="a5f16-148">Integración con el equipo telefónico existente (centrales de conmutación privada [PBX], por ejemplo).</span><span class="sxs-lookup"><span data-stu-id="a5f16-148">Integration with existing phone equipment, such as private branch exchanges (PBXs).</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="a5f16-149">Lync Server hospedado por el proveedor</span><span class="sxs-lookup"><span data-stu-id="a5f16-149">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="a5f16-p103">En esta implementación, todo está en manos del proveedor. El diagrama adjunto muestra una red del proveedor, incluyendo sus servidores y equipo, con una conexión a un entorno local.</span><span class="sxs-lookup"><span data-stu-id="a5f16-p103">In this deployment, your provider owns everything. The accompanying diagram shows a provider's network including their servers and equipment with a connection to an on-premises environment.</span></span>
  
<span data-ttu-id="a5f16-152">Descripción de las características y funcionalidades:</span><span class="sxs-lookup"><span data-stu-id="a5f16-152">Description of features and functionality:</span></span>
  
- <span data-ttu-id="a5f16-153">Planeamiento de la capacidad y ajuste del tamaño.</span><span class="sxs-lookup"><span data-stu-id="a5f16-153">Capacity planning and sizing.</span></span>
    
- <span data-ttu-id="a5f16-154">Adquisición y configuración de servidores.</span><span class="sxs-lookup"><span data-stu-id="a5f16-154">Server acquisition and setup.</span></span>
    
- <span data-ttu-id="a5f16-155">Implementación.</span><span class="sxs-lookup"><span data-stu-id="a5f16-155">Deployment.</span></span>
    
- <span data-ttu-id="a5f16-156">Escalado horizontal, revisiones y operaciones.</span><span class="sxs-lookup"><span data-stu-id="a5f16-156">Scaling out, patching, and operations.</span></span>
    
- <span data-ttu-id="a5f16-157">Copias de seguridad de datos.</span><span class="sxs-lookup"><span data-stu-id="a5f16-157">Backing up data.</span></span>
    
- <span data-ttu-id="a5f16-158">Mantenimiento de conmutación por error y recuperación ante desastres.</span><span class="sxs-lookup"><span data-stu-id="a5f16-158">Maintaining failover and disaster recovery.</span></span>
    
- <span data-ttu-id="a5f16-159">Integración con el equipo telefónico existente (centrales de conmutación privada [PBX], por ejemplo).</span><span class="sxs-lookup"><span data-stu-id="a5f16-159">Integration with existing phone equipment, such as private branch exchanges (PBXs).</span></span>
    
- <span data-ttu-id="a5f16-160">Además, el proveedor puede:</span><span class="sxs-lookup"><span data-stu-id="a5f16-160">In addition, the provider can:</span></span>
    
  - <span data-ttu-id="a5f16-161">Instalar sus servidores y equipo en su propia red con una conexión a las instalaciones de la organización (línea continua).</span><span class="sxs-lookup"><span data-stu-id="a5f16-161">Install their servers and equipment in their own network with a connection to your premises (solid line).</span></span>
    
  - <span data-ttu-id="a5f16-162">Instalar sus servidores directamente en las instalaciones de la organización (línea discontinua).</span><span class="sxs-lookup"><span data-stu-id="a5f16-162">Install their servers on your premises (dotted line).</span></span>
    
### <a name="benefits-of-implementing-each-deployment-option"></a><span data-ttu-id="a5f16-163">Ventajas de la implementación de cada opción de implementación</span><span class="sxs-lookup"><span data-stu-id="a5f16-163">Benefits of implementing each deployment option</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="a5f16-164">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="a5f16-164">Lync Online (Office 365)</span></span>

- <span data-ttu-id="a5f16-165">Carga operativa nula a los servidores locales o al software de los servidores.</span><span class="sxs-lookup"><span data-stu-id="a5f16-165">No operational burden of on-premises servers or server software.</span></span>
    
- <span data-ttu-id="a5f16-166">Capacidades de comunicación de Lync Server 2013 como servicio basado en la nube.</span><span class="sxs-lookup"><span data-stu-id="a5f16-166">Communication capabilities of Lync Server 2013 as a cloud-based service.</span></span>
    
- <span data-ttu-id="a5f16-167">Presencia de Lync, mensajería instantánea, llamadas de audio y vídeo, reuniones en línea enriquecidas y capacidades de conferencias web extensas.</span><span class="sxs-lookup"><span data-stu-id="a5f16-167">Lync presence, instant messaging, audio and video calling, rich online meetings, and extensive web conferencing capabilities.</span></span>
    
- <span data-ttu-id="a5f16-168">Útil para organizaciones dispersas geográficamente o con los empleados que se desplazan la mayor parte del tiempo.</span><span class="sxs-lookup"><span data-stu-id="a5f16-168">Used with geographically-dispersed organizations or with primarily mobile employees.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="a5f16-169">Implementación híbrida de Lync Online/Server (dominio dividido)</span><span class="sxs-lookup"><span data-stu-id="a5f16-169">Lync Online/Server Hybrid (split domain)</span></span>

- <span data-ttu-id="a5f16-170">Uso de Lync Online con usuarios remotos y para la integración con sus asociados comerciales.</span><span class="sxs-lookup"><span data-stu-id="a5f16-170">Use Lync Online for remote users and integration with business partners.</span></span>
    
- <span data-ttu-id="a5f16-171">Migración sencilla de Lync local a Lync Online.</span><span class="sxs-lookup"><span data-stu-id="a5f16-171">Facilitate a migration from Lync on-premises to Lync Online.</span></span>
    
- <span data-ttu-id="a5f16-172">Compatibilidad con sitios remotos sin usar un equipo de la sucursal.</span><span class="sxs-lookup"><span data-stu-id="a5f16-172">Support remote sites without using a branch office appliance.</span></span>
    
- <span data-ttu-id="a5f16-173">Facilidad para agregar compatibilidad con Lync a las nuevas adquisiciones de la empresa.</span><span class="sxs-lookup"><span data-stu-id="a5f16-173">Ease of adding Lync support for new business acquisitions.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="a5f16-174">Lync Server</span><span class="sxs-lookup"><span data-stu-id="a5f16-174">Lync Server</span></span>

- <span data-ttu-id="a5f16-175">Soluciones de nube privada.</span><span class="sxs-lookup"><span data-stu-id="a5f16-175">Private cloud solutions.</span></span>
    
- <span data-ttu-id="a5f16-176">Soluciones muy personalizadas.</span><span class="sxs-lookup"><span data-stu-id="a5f16-176">Highly customized solutions.</span></span>
    
- <span data-ttu-id="a5f16-177">Soluciones heredadas con componentes de terceros que dependen de hardware y software no compatible con Lync Online.</span><span class="sxs-lookup"><span data-stu-id="a5f16-177">Legacy solutions with third-party components that depend on hardware and software that are not supported by Lync Online.</span></span>
    
- <span data-ttu-id="a5f16-178">Restricciones de privacidad que evitan la sincronización de cuentas de AD DS con Office 365.</span><span class="sxs-lookup"><span data-stu-id="a5f16-178">Privacy restrictions that prevent synchronization of AD DS accounts with Office 365.</span></span>
    
- <span data-ttu-id="a5f16-179">Ideal para organizaciones que quieren tener el control completo de la plataforma y la solución.</span><span class="sxs-lookup"><span data-stu-id="a5f16-179">Organizations that desire control of the entire platform and solution.</span></span>
    
- <span data-ttu-id="a5f16-180">Sustitución de PBX por Enterprise Voice de Lync.</span><span class="sxs-lookup"><span data-stu-id="a5f16-180">PBX replacement with Lync Enterprise Voice.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="a5f16-181">Lync Server hospedado por el proveedor</span><span class="sxs-lookup"><span data-stu-id="a5f16-181">Provider-Hosted Lync Server</span></span>

- <span data-ttu-id="a5f16-182">Ideal para organizaciones que desean la funcionalidad de Lync Server, pero quieren subcontratar su implementación y mantenimiento.</span><span class="sxs-lookup"><span data-stu-id="a5f16-182">Organizations that want Lync Server functionality but want to outsource its deployment and maintenance.</span></span>
    
- <span data-ttu-id="a5f16-183">Soluciones basadas en el proveedor.</span><span class="sxs-lookup"><span data-stu-id="a5f16-183">Provider-based solutions.</span></span>
    
- <span data-ttu-id="a5f16-184">Soluciones muy personalizadas.</span><span class="sxs-lookup"><span data-stu-id="a5f16-184">Highly customized solutions.</span></span>
    
- <span data-ttu-id="a5f16-185">Soluciones heredadas con componentes de terceros que dependen de hardware y software no compatible con Lync Online.</span><span class="sxs-lookup"><span data-stu-id="a5f16-185">Legacy solutions with third-party components that depend on hardware and software that are not supported by Lync Online.</span></span>
    
- <span data-ttu-id="a5f16-186">Sustitución de PBX por Enterprise Voice de Lync.</span><span class="sxs-lookup"><span data-stu-id="a5f16-186">PBX replacement with Lync Enterprise Voice.</span></span>
    
### <a name="license-requirements"></a><span data-ttu-id="a5f16-187">Requisitos de licencia</span><span class="sxs-lookup"><span data-stu-id="a5f16-187">License requirements</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="a5f16-188">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="a5f16-188">Lync Online (Office 365)</span></span>

<span data-ttu-id="a5f16-189">Modelo de suscripción.</span><span class="sxs-lookup"><span data-stu-id="a5f16-189">Subscription model.</span></span>
  
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="a5f16-190">Implementación híbrida de Lync Online/Server (dominio dividido)</span><span class="sxs-lookup"><span data-stu-id="a5f16-190">Lync Online/Server Hybrid (split domain)</span></span>

- <span data-ttu-id="a5f16-p104">Office 365: modelo de suscripción. No se requieren licencias adicionales.</span><span class="sxs-lookup"><span data-stu-id="a5f16-p104">Office 365 — Subscription model. No additional licenses needed.</span></span> 
    
- <span data-ttu-id="a5f16-193">Implementación local: se aplican todas las licencias locales.</span><span class="sxs-lookup"><span data-stu-id="a5f16-193">On-premises — All on-premises licenses apply.</span></span> 
    
#### <a name="lync-server"></a><span data-ttu-id="a5f16-194">Lync Server</span><span class="sxs-lookup"><span data-stu-id="a5f16-194">Lync Server</span></span>

- <span data-ttu-id="a5f16-195">Sistema operativo del servidor</span><span class="sxs-lookup"><span data-stu-id="a5f16-195">Server Operating System</span></span>
    
- <span data-ttu-id="a5f16-196">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a5f16-196">SQL Server</span></span>
    
- <span data-ttu-id="a5f16-197">Licencia de Lync Server 2013</span><span class="sxs-lookup"><span data-stu-id="a5f16-197">Lync 2013 Server License</span></span>
    
- <span data-ttu-id="a5f16-198">Licencia de acceso de cliente de Lync 2013</span><span class="sxs-lookup"><span data-stu-id="a5f16-198">Lync 2013 Client Access License</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="a5f16-199">Lync Server hospedado por el proveedor</span><span class="sxs-lookup"><span data-stu-id="a5f16-199">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="a5f16-200">Los costos se basan en el acuerdo con el proveedor de soluciones de Lync.</span><span class="sxs-lookup"><span data-stu-id="a5f16-200">Costs are based on the agreement with your Lync solution provider.</span></span>
  
### <a name="architecture-tasks"></a><span data-ttu-id="a5f16-201">Tareas de arquitectura</span><span class="sxs-lookup"><span data-stu-id="a5f16-201">Architecture tasks</span></span>

<span data-ttu-id="a5f16-202">Esta sección muestra las tareas de arquitectura para cada opción de implementación.</span><span class="sxs-lookup"><span data-stu-id="a5f16-202">This section lists the architectural tasks for each deployment option.</span></span>
  
#### <a name="lync-online-office-365"></a><span data-ttu-id="a5f16-203">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="a5f16-203">Lync Online (Office 365)</span></span>

- <span data-ttu-id="a5f16-204">Planee y diseñe la sincronización de directorios.</span><span class="sxs-lookup"><span data-stu-id="a5f16-204">Plan and design directory synchronization.</span></span>
    
- <span data-ttu-id="a5f16-205">Garantice la capacidad de la red y la disponibilidad a través de firewalls, servidores proxy, puertas de enlace y vínculos WAN.</span><span class="sxs-lookup"><span data-stu-id="a5f16-205">Ensure network capacity and availability through firewalls, proxy servers, gateways, and across WAN links.</span></span>
    
- <span data-ttu-id="a5f16-206">Adquirir certificados SSL de terceros para proporcionar seguridad empresarial para las ofertas de servicio de Office 365.</span><span class="sxs-lookup"><span data-stu-id="a5f16-206">Acquire third-party SSL certificates to provide enterprise-security for Office 365 service offerings.</span></span>
    
- <span data-ttu-id="a5f16-207">Decida si desea conectarse a Office 365 con el protocolo de Internet versión 6 (IPv6).</span><span class="sxs-lookup"><span data-stu-id="a5f16-207">Decide if you want to connect to Office 365 with Internet Protocol version 6 (IPv6).</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="a5f16-208">Implementación híbrida de Lync Online/Server (dominio dividido)</span><span class="sxs-lookup"><span data-stu-id="a5f16-208">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="a5f16-209">Además de las tareas para entornos Office 365 y locales:</span><span class="sxs-lookup"><span data-stu-id="a5f16-209">In addition to tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="a5f16-210">Determine el grado de integración de características que quiere usar con las versiones locales y en línea de Exchange Server y SharePoint.</span><span class="sxs-lookup"><span data-stu-id="a5f16-210">Determine how much feature integration you want to use with on-premises and online versions of Exchange Server and SharePoint.</span></span>
    
- <span data-ttu-id="a5f16-211">Si es necesario, determine el servidor proxy que se usará para las solicitudes de Office 365.</span><span class="sxs-lookup"><span data-stu-id="a5f16-211">If required, determine which proxy server device will be used for requests from Office 365.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="a5f16-212">Lync Server</span><span class="sxs-lookup"><span data-stu-id="a5f16-212">Lync Server</span></span>

<span data-ttu-id="a5f16-213">Diseñe el entorno de Lync en un entorno local existente:</span><span class="sxs-lookup"><span data-stu-id="a5f16-213">Design the Lync environment in an existing on-premises environment:</span></span>
  
- <span data-ttu-id="a5f16-214">Topología de Lync para oficinas centrales y sucursales.</span><span class="sxs-lookup"><span data-stu-id="a5f16-214">Lync topology for central and branch offices.</span></span>
    
- <span data-ttu-id="a5f16-215">Hardware del servidor (virtualización incluida).</span><span class="sxs-lookup"><span data-stu-id="a5f16-215">Server hardware, including virtualization.</span></span>
    
- <span data-ttu-id="a5f16-216">Integración con los Servicios de dominio de Active Directory (AD DS) y DNS.</span><span class="sxs-lookup"><span data-stu-id="a5f16-216">Integration with Active Directory Domain Services (AD DS) and DNS.</span></span>
    
- <span data-ttu-id="a5f16-217">Equilibrio de carga para granjas de servidores de Lync.</span><span class="sxs-lookup"><span data-stu-id="a5f16-217">Load balancing for Lync server pools.</span></span>
    
- <span data-ttu-id="a5f16-218">Conmutación por error y recuperación ante desastres.</span><span class="sxs-lookup"><span data-stu-id="a5f16-218">Failover and disaster recovery.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="a5f16-219">Lync Server hospedado por el proveedor</span><span class="sxs-lookup"><span data-stu-id="a5f16-219">Provider-Hosted Lync Server</span></span>

- <span data-ttu-id="a5f16-220">Para una instalación basada en la nube, determine la conexión a la red del proveedor de servicios.</span><span class="sxs-lookup"><span data-stu-id="a5f16-220">For a cloud-based installation, determine the connection to the service provider's network.</span></span>
    
- <span data-ttu-id="a5f16-221">Para una instalación local, determine la ubicación de los servidores de Lync del proveedor en su red.</span><span class="sxs-lookup"><span data-stu-id="a5f16-221">For an on-premises installation, determine the placement of the provider's Lync servers on your network.</span></span>
    
- <span data-ttu-id="a5f16-222">Para ambos tipos, determine la integración con AD DS y con el equipo de PBX.</span><span class="sxs-lookup"><span data-stu-id="a5f16-222">For both types, determine the integration with AD DS and your PBX equipment.</span></span>
    
### <a name="it-pro-responsibilities"></a><span data-ttu-id="a5f16-223">Responsabilidades del profesional de TI</span><span class="sxs-lookup"><span data-stu-id="a5f16-223">IT Pro responsibilities</span></span>

<span data-ttu-id="a5f16-224">Esta sección muestra las responsabilidades del profesional de TI para cada opción de implementación.</span><span class="sxs-lookup"><span data-stu-id="a5f16-224">This section lists the IT Pro responsibilities for each deployment option.</span></span>
  
#### <a name="lync-online-office-365"></a><span data-ttu-id="a5f16-225">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="a5f16-225">Lync Online (Office 365)</span></span>

<span data-ttu-id="a5f16-226">Implemente y administre Lync Online (Office 365):</span><span class="sxs-lookup"><span data-stu-id="a5f16-226">Deploy and manage Lync Online (Office 365):</span></span>
  
- <span data-ttu-id="a5f16-227">Implemente el plan de sincronización de directorios.</span><span class="sxs-lookup"><span data-stu-id="a5f16-227">Implement the directory synchronization plan.</span></span>
    
- <span data-ttu-id="a5f16-228">Planee e implemente enrutamiento y registros DNS internos y externos.</span><span class="sxs-lookup"><span data-stu-id="a5f16-228">Plan and implement internal and external DNS records and routing.</span></span>
    
- <span data-ttu-id="a5f16-229">Configure el proxy o el firewall conforme a los requisitos de dirección IP y URL de Office 365.</span><span class="sxs-lookup"><span data-stu-id="a5f16-229">Configure your proxy or firewall for Office 365 IP address and URL requirements.</span></span>
    
- <span data-ttu-id="a5f16-230">Administre las cuentas de usuario y la configuración de Lync Online.</span><span class="sxs-lookup"><span data-stu-id="a5f16-230">Administer user accounts and Lync Online settings.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="a5f16-231">Implementación híbrida de Lync Online/Server (dominio dividido)</span><span class="sxs-lookup"><span data-stu-id="a5f16-231">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="a5f16-232">Además de las tareas para entornos Office 365 y locales:</span><span class="sxs-lookup"><span data-stu-id="a5f16-232">In addition to tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="a5f16-233">Configure el servidor proxy, si es necesario.</span><span class="sxs-lookup"><span data-stu-id="a5f16-233">Configure the proxy server device, if required.</span></span>
    
- <span data-ttu-id="a5f16-234">Configure la integración de características con las versiones locales y en línea de Exchange Server y SharePoint.</span><span class="sxs-lookup"><span data-stu-id="a5f16-234">Configure the integration of features with on-premises and online versions of Exchange Server and SharePoint.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="a5f16-235">Lync Server</span><span class="sxs-lookup"><span data-stu-id="a5f16-235">Lync Server</span></span>

<span data-ttu-id="a5f16-236">Implemente y administre el entorno local de Lync:</span><span class="sxs-lookup"><span data-stu-id="a5f16-236">Deploy and manage Lync Server in an on-premises environment:</span></span>
  
- <span data-ttu-id="a5f16-237">Aprovisione los servidores.</span><span class="sxs-lookup"><span data-stu-id="a5f16-237">Provision the servers.</span></span>
    
- <span data-ttu-id="a5f16-238">Implemente la topología de Lync.</span><span class="sxs-lookup"><span data-stu-id="a5f16-238">Deploy the Lync topology.</span></span>
    
- <span data-ttu-id="a5f16-239">Actualice los servidores de Lync.</span><span class="sxs-lookup"><span data-stu-id="a5f16-239">Update Lync servers.</span></span>
    
- <span data-ttu-id="a5f16-240">Agregue o quite servidores de la topología según sea necesario con base en el uso.</span><span class="sxs-lookup"><span data-stu-id="a5f16-240">Add or remove topology servers as needed based on utilization.</span></span>
    
- <span data-ttu-id="a5f16-241">Implemente el entorno de conmutación por error y recuperación ante desastres.</span><span class="sxs-lookup"><span data-stu-id="a5f16-241">Implement the failover and disaster recovery environment.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="a5f16-242">Lync Server hospedado por el proveedor</span><span class="sxs-lookup"><span data-stu-id="a5f16-242">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="a5f16-243">Colabore con el proveedor para:</span><span class="sxs-lookup"><span data-stu-id="a5f16-243">Work with the provider to:</span></span>
  
- <span data-ttu-id="a5f16-244">Integrar Lync Server a su red.</span><span class="sxs-lookup"><span data-stu-id="a5f16-244">Integrate Lync Server into your network.</span></span>
    
- <span data-ttu-id="a5f16-245">Integre Lync Server con otros productos de Microsoft o soluciones personalizadas.</span><span class="sxs-lookup"><span data-stu-id="a5f16-245">Integrate Lync Server with other Microsoft products or custom solutions.</span></span>
    
- <span data-ttu-id="a5f16-246">Supervisar el cumplimiento del contrato de nivel de servicio (SLA) con el proveedor.</span><span class="sxs-lookup"><span data-stu-id="a5f16-246">Monitor adherence with provider service level agreement (SLA).</span></span>
    
## <a name="two-example-scenarios-for-deploying-lync-2013"></a><span data-ttu-id="a5f16-247">Dos ejemplos de escenarios de implementación de Lync 2013</span><span class="sxs-lookup"><span data-stu-id="a5f16-247">Two example scenarios for deploying Lync 2013</span></span>

### <a name="directory-synchronization-components-in-microsoft-azure"></a><span data-ttu-id="a5f16-248">Componentes de sincronización de directorios en Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="a5f16-248">Directory Synchronization components in Microsoft Azure</span></span>

<span data-ttu-id="a5f16-249">La implementación de componentes de sincronización de directorios de Office 365 en Azure es más rápida gracias a la posibilidad de implementar máquinas virtuales a petición.</span><span class="sxs-lookup"><span data-stu-id="a5f16-249">Deploying Office 365 directory synchronization components in Azure is faster due to the ability to deploy virtual machines on-demand.</span></span>
  
<span data-ttu-id="a5f16-250">El diagrama correspondiente muestra Lync Online con un inquilino de Azure Active Directory que sincroniza nombres y contraseñas de cuentas entre el entorno de Active Directory (AD DS) y el inquilino de Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="a5f16-250">The accompanying diagram shows Lync Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span>
  
 <span data-ttu-id="a5f16-p105">**Solo servidor de sincronización de directorios**. En lugar de implementar el servidor de sincronización de directorios de 64 bits en el entorno local, se aprovisiona una máquina virtual en Azure a través de Internet.</span><span class="sxs-lookup"><span data-stu-id="a5f16-p105">**Directory synchronization server only**. Instead of deploying the 64-bit directory synchronization server in your on-premises environment, you provision a virtual machine in Azure over the Internet.</span></span>
  
 <span data-ttu-id="a5f16-p106">**Sincronización de directorios + AD FS**. Gracias a esta opción se admiten las identidades federadas de Office 365 sin necesidad de agregar hardware a la infraestructura local. También ofrece resistencia si el entorno Active Directory local no está disponible. Las características de esta opción incluyen:</span><span class="sxs-lookup"><span data-stu-id="a5f16-p106">**Directory synchronization + AD FS**. This option allows you to support Office 365 federated identities (SSO) without adding hardware to your on-premises infrastructure. It also provides resiliency if the on-premises Active Directory environment is unavailable. The features of this option include:</span></span>
  
- <span data-ttu-id="a5f16-257">Ejecución de componentes de integración de directorios como máquinas virtuales de Azure.</span><span class="sxs-lookup"><span data-stu-id="a5f16-257">Directory integration components run as Azure virtual machines.</span></span>
    
- <span data-ttu-id="a5f16-258">AD FS se publica en Internet a través de servidores proxy de AD FS en máquinas virtuales de Azure.</span><span class="sxs-lookup"><span data-stu-id="a5f16-258">AD FS is published to the Internet through AD FS proxies running as Azure virtual machines.</span></span>
    
- <span data-ttu-id="a5f16-259">En el caso de usuarios que se conectan desde ubicaciones no especificadas, el tráfico de autenticación de cliente se controla a través de servidores de AD FS y servidores proxy que se encuentran implementados en máquinas virtuales de Azure.</span><span class="sxs-lookup"><span data-stu-id="a5f16-259">Client authentication traffic, for users that are connecting from any location, is handled by AD FS servers and proxies that are deployed as Azure virtual machines.</span></span>
    
### <a name="lync-integration-with-exchange-and-sharepoint-in-office-365"></a><span data-ttu-id="a5f16-260">Integración de Lync con Exchange y SharePoint en Office 365</span><span class="sxs-lookup"><span data-stu-id="a5f16-260">Lync integration with Exchange and SharePoint in Office 365</span></span>

#### <a name="lync-server-with-exchange-online-and-sharepoint-online"></a><span data-ttu-id="a5f16-261">Lync Server con Exchange Online y SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="a5f16-261">Lync Server with Exchange Online and SharePoint Online</span></span>

<span data-ttu-id="a5f16-262">En el diagrama adjunto se muestra Office 365 con Exchange Online y SharePoint Online, conectado a una granja de servidores de Lync Server 2013 local.</span><span class="sxs-lookup"><span data-stu-id="a5f16-262">The accompanying diagram shows Office 365 with Exchange Online and SharePoint Online connected to an on-premises Lync Server 2013 farm.</span></span>
  
<span data-ttu-id="a5f16-263">Las ventajas de esta implementación le permiten:</span><span class="sxs-lookup"><span data-stu-id="a5f16-263">The advantages of this deployment allow you to:</span></span>
  
- <span data-ttu-id="a5f16-264">Usar el conjunto completo de características de Lync Server 2013.</span><span class="sxs-lookup"><span data-stu-id="a5f16-264">Use the full feature set of Lync Server 2013.</span></span>
    
- <span data-ttu-id="a5f16-265">Aprovechar su equipo telefónico local existente (por ejemplo los sistemas PBX).</span><span class="sxs-lookup"><span data-stu-id="a5f16-265">Leverage your existing on-premises phone equipment, such as PBXs.</span></span>
    
- <span data-ttu-id="a5f16-266">Usar Exchange Online para el correo electrónico, lo que reduce la carga de almacenamiento y de los servidores de correo electrónico locales.</span><span class="sxs-lookup"><span data-stu-id="a5f16-266">Use Exchange Online for email, off-loading the burden of on-premises email servers and storage.</span></span>
    
- <span data-ttu-id="a5f16-267">Usar SharePoint Online para la colaboración, lo que reduce la carga de mantenimiento de servidores de SharePoint locales.</span><span class="sxs-lookup"><span data-stu-id="a5f16-267">Use SharePoint Online for collaboration, off-loading the burden of maintaining on-premises SharePoint servers.</span></span>
    
- <span data-ttu-id="a5f16-268">Usar las características integradas de Lync, Exchange y SharePoint, incluida la mensajería unificada (UM) en Office 365.</span><span class="sxs-lookup"><span data-stu-id="a5f16-268">Use Lync, Exchange, and SharePoint integrated features, including Unified Messaging (UM) in Office 365.</span></span>
    
#### <a name="exchange-server-with-lync-online"></a><span data-ttu-id="a5f16-269">Exchange Server con Lync Online</span><span class="sxs-lookup"><span data-stu-id="a5f16-269">Exchange Server with Lync Online</span></span>

<span data-ttu-id="a5f16-270">En el diagrama adjunto se muestra Office 365 con Lync Online, conectado a una granja de servidores de Exchange Server local.</span><span class="sxs-lookup"><span data-stu-id="a5f16-270">The accompanying diagram shows Office 365 with Lync Online connected to an on-premises Exchange Server farm.</span></span>
  
<span data-ttu-id="a5f16-271">Las ventajas de esta implementación le permiten:</span><span class="sxs-lookup"><span data-stu-id="a5f16-271">The advantages of this deployment allow you to:</span></span>
  
- <span data-ttu-id="a5f16-272">Aprovechar su actual infraestructura de Exchange.</span><span class="sxs-lookup"><span data-stu-id="a5f16-272">Leverage your existing Exchange infrastructure.</span></span>
    
- <span data-ttu-id="a5f16-273">Usar Lync Online para funciones de presencia, mensajería instantánea y conferencias.</span><span class="sxs-lookup"><span data-stu-id="a5f16-273">Use Lync Online for presence, instant messaging, and conferencing capabilities.</span></span>
    

