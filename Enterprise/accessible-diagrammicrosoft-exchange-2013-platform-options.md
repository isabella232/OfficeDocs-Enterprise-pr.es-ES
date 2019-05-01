---
title: Diagrama accesible Opciones de plataformas de Microsoft Exchange 2013
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 129f4e45-647e-4cf1-92a6-4d86d8396e73
description: Este artículo es una versión de texto accesible del diagrama con el nombre Opciones de plataforma de Microsoft Exchange 2013, que está disponible en Diagramas técnicos.
ms.openlocfilehash: e1c4957c9152c5a23008c657d7e2d0d47b5cce0f
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487807"
---
# <a name="accessible-diagram---microsoft-exchange-2013-platform-options"></a><span data-ttu-id="3b64d-103">Diagrama accesible: Opciones de plataformas de Microsoft Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="3b64d-103">Accessible diagram - Microsoft Exchange 2013 Platform Options</span></span>

<span data-ttu-id="3b64d-104">**Resumen:** este artículo es una versión de texto accesible del diagrama “Opciones de plataformas de Microsoft Exchange 2013”, que está disponible en [Diagramas técnicos](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span><span class="sxs-lookup"><span data-stu-id="3b64d-104">**Summary:** This article is an accessible text version of the diagram named Microsoft Exchange 2013 Platform Options, which is available at [Technical Diagrams](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span></span>
  
<span data-ttu-id="3b64d-105">Este póster describe lo que los arquitectos y responsables de decisiones empresariales (BDM) necesitan saber sobre implementaciones de Exchange Online e Exchange Server. Incluye lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="3b64d-105">This poster describes what business decision makers (BDMs) and architects need to know about Exchange Online and Exchange Server deployments and includes:</span></span> 
  
- <span data-ttu-id="3b64d-106">Una comparación de cuatro opciones de plataforma disponibles para Exchange 2013: Exchange Online (Office 365), Exchange Hybrid, Exchange Server local e Exchange hospedado por el proveedor.</span><span class="sxs-lookup"><span data-stu-id="3b64d-106">A comparison of four available platform options for Exchange 2013: Exchange Online (Office 365), Exchange Hybrid, Exchange Server on-premises, and Provider-Hosted Exchange.</span></span> 
    
- <span data-ttu-id="3b64d-107">Descripciones de tres características nuevas o actualizadas en Exchange 2013.</span><span class="sxs-lookup"><span data-stu-id="3b64d-107">Descriptions of three new or updated features in Exchange 2013.</span></span> 
    
## <a name="comparison-of-four-different-deployments-for-the-exchange-2013-platform"></a><span data-ttu-id="3b64d-108">Comparación de cuatro implementaciones diferentes para la plataforma de Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="3b64d-108">Comparison of four different deployments for the Exchange 2013 platform</span></span>

<span data-ttu-id="3b64d-109">La comparación proporciona información sobre cada opción de implementación en las siguientes áreas:</span><span class="sxs-lookup"><span data-stu-id="3b64d-109">The comparison provides information about each deployment option in the following areas:</span></span> 
  
- <span data-ttu-id="3b64d-110">Información general sobre las diferentes características de implementación</span><span class="sxs-lookup"><span data-stu-id="3b64d-110">An overview of the different deployment features</span></span> 
    
- <span data-ttu-id="3b64d-111">Ventajas de la implementación de cada opción de implementación</span><span class="sxs-lookup"><span data-stu-id="3b64d-111">Benefits of implementing each deployment option</span></span> 
    
- <span data-ttu-id="3b64d-112">Requisitos de licencia</span><span class="sxs-lookup"><span data-stu-id="3b64d-112">Licensing requirements</span></span> 
    
- <span data-ttu-id="3b64d-113">Tareas de arquitectura requeridas</span><span class="sxs-lookup"><span data-stu-id="3b64d-113">Required architectural tasks</span></span> 
    
- <span data-ttu-id="3b64d-114">Responsabilidades del profesional de TI para implementar cada opción de implementación</span><span class="sxs-lookup"><span data-stu-id="3b64d-114">IT Pro responsibilities for implementing each deployment option</span></span> 
    
### <a name="overview"></a><span data-ttu-id="3b64d-115">Información general</span><span class="sxs-lookup"><span data-stu-id="3b64d-115">Overview</span></span>

#### <a name="exchange-online-office-365"></a><span data-ttu-id="3b64d-116">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="3b64d-116">Exchange Online (Office 365)</span></span>

<span data-ttu-id="3b64d-117">Se gana eficiencia y reducen costes con Office 365.</span><span class="sxs-lookup"><span data-stu-id="3b64d-117">You gain efficiency and reduce costs with Office 365.</span></span>
  
<span data-ttu-id="3b64d-p101">El diagrama correspondiente muestra Exchange Online con un inquilino de Azure Active Directory que sincroniza nombres y contraseñas de cuentas entre el entorno de Servicios de dominio de Active Directory (AD DS) y el inquilino de Azure Active Directory. Los Servicios de federación de Active Directory (AD FS) son necesarios para el inicio de sesión único.</span><span class="sxs-lookup"><span data-stu-id="3b64d-p101">The accompanying diagram shows Exchange Online with an Azure Active Directory tenant which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant. Active Directory Federation Services (AD FS) is necessary for single sign-on.</span></span> 
  
<span data-ttu-id="3b64d-120">Descripción de las características y funcionalidades:</span><span class="sxs-lookup"><span data-stu-id="3b64d-120">Description of features and functionality:</span></span>
  
- <span data-ttu-id="3b64d-121">Microsoft controla el funcionamiento de los servidores y el software de servidor.</span><span class="sxs-lookup"><span data-stu-id="3b64d-121">The operation of servers and server software is handled by Microsoft.</span></span>
    
- <span data-ttu-id="3b64d-122">Conjunto enriquecido de Exchange Server 2013 como servicio basado en nube.</span><span class="sxs-lookup"><span data-stu-id="3b64d-122">Rich feature set of Exchange Server 2013 as a cloud-based service.</span></span>
    
- <span data-ttu-id="3b64d-123">Siempre actualizado con las características más recientes.</span><span class="sxs-lookup"><span data-stu-id="3b64d-123">Always up-to-date with the newest features.</span></span>
    
- <span data-ttu-id="3b64d-124">Exchange Online Protection (EOP) se incluye para la protección de correo no deseado y contra malware.</span><span class="sxs-lookup"><span data-stu-id="3b64d-124">Exchange Online Protection (EOP) is included for anti-spam/anti-malware protection.</span></span>
    
- <span data-ttu-id="3b64d-125">Alta disponibilidad integrada con un contrato de nivel de servicio (SLA) del 99,9 %.</span><span class="sxs-lookup"><span data-stu-id="3b64d-125">Built-in high availability with a 99.9% Service Level Agreement (SLA).</span></span>
    
- <span data-ttu-id="3b64d-p102">Sincronización de directorios que incluye contraseñas entre los Servicios de dominio de Active Directory (AD DS) locales y el inquilino de Azure Active Directory. Los Servicios de federación de Active Directory (AD FS) son necesarios para el inicio de sesión único.</span><span class="sxs-lookup"><span data-stu-id="3b64d-p102">Directory synchronization including passwords between the on-premises Active Directory Domain Services (AD DS) and the Azure Active Directory tenant. Active Directory Federation Services (AD FS) is necessary for single sign-on.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="3b64d-128">Exchange Hybrid</span><span class="sxs-lookup"><span data-stu-id="3b64d-128">Exchange Hybrid</span></span>

<span data-ttu-id="3b64d-129">Puede aprovechar las ventajas de Office 365 mientras mantiene Exchange Server local.</span><span class="sxs-lookup"><span data-stu-id="3b64d-129">You can leverage the benefits of Office 365 while maintaining Exchange Server on-premises.</span></span>
  
<span data-ttu-id="3b64d-p103">El diagrama correspondiente muestra Office 365 con Exchange Online donde algunos usuarios están alojados de forma local y algunos usuarios están alojados en línea. También muestra un inquilino de Azure Active Directory que sincroniza nombres y contraseñas de cuentas entre el entorno de Servicios de dominio de Active Directory (AD DS) y el inquilino de Azure. Active Directory.</span><span class="sxs-lookup"><span data-stu-id="3b64d-p103">The accompanying diagram shows Office 365 with Exchange Online where some users are homed on-premises and some users are homed online. It also shows an Azure Active Directory tenant which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span>
  
<span data-ttu-id="3b64d-132">Descripción de las características y funcionalidades:</span><span class="sxs-lookup"><span data-stu-id="3b64d-132">Description of features and functionality:</span></span>
  
- <span data-ttu-id="3b64d-133">Algunos usuarios están alojados de forma local y algunos usuarios están alojados en línea. Los usuarios comparten el mismo espacio de direcciones de correo electrónico.</span><span class="sxs-lookup"><span data-stu-id="3b64d-133">Some users are homed on-premises and some users are homed online, and users share the same e-mail address space.</span></span>
    
- <span data-ttu-id="3b64d-134">Aprovecha la infraestructura existente de Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="3b64d-134">Leverages your existing Exchange Server infrastructure.</span></span>
    
- <span data-ttu-id="3b64d-135">Migre desde Exchange local a Exchange Online con el transcurso del tiempo, según su programación.</span><span class="sxs-lookup"><span data-stu-id="3b64d-135">Migrate from Exchange on-premises to Exchange Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="3b64d-136">Integre con otras aplicaciones Office 365, incluidas Lync Online y SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="3b64d-136">Integrate with other Office 365 applications, including Lync Online and SharePoint Online.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="3b64d-137">Exchange Server local</span><span class="sxs-lookup"><span data-stu-id="3b64d-137">Exchange Server on-premises</span></span>

<span data-ttu-id="3b64d-138">Puede diseñar y administrar su propia infraestructura de Exchange Server 2013.</span><span class="sxs-lookup"><span data-stu-id="3b64d-138">You can design and manage your own Exchange Server 2013 infrastructure.</span></span>
  
<span data-ttu-id="3b64d-139">El diagrama correspondiente muestra una infraestructura de Exchange Server con un entorno de Active Directory Domain Services (AD DS) local donde los usuarios están alojados de forma local.</span><span class="sxs-lookup"><span data-stu-id="3b64d-139">The accompanying diagram shows an Exchange Server infrastructure with an on-premises Active Directory Domain Services (AD DS) environment where users are homed on-premises.</span></span>
  
<span data-ttu-id="3b64d-140">Descripción de las características y funcionalidades:</span><span class="sxs-lookup"><span data-stu-id="3b64d-140">Description of features and functionality:</span></span>
  
- <span data-ttu-id="3b64d-141">El mayor grado de control y personalización para su configuración.</span><span class="sxs-lookup"><span data-stu-id="3b64d-141">Greatest degree of control and customization for your configuration.</span></span>
    
- <span data-ttu-id="3b64d-142">Sin dependencia en mantener la afinidad de sesión en la capa de equilibrio de carga.</span><span class="sxs-lookup"><span data-stu-id="3b64d-142">No dependency on maintaining session affinity at the load balancing layer.</span></span>
    
- <span data-ttu-id="3b64d-143">Alta disponibilidad y resistencia de sitios sencillas con grupos de disponibilidad de base de datos (DAG).</span><span class="sxs-lookup"><span data-stu-id="3b64d-143">Simple high availability and site resilience using database availability groups (DAGs).</span></span>
    
- <span data-ttu-id="3b64d-144">Disponibilidad administrada que ayuda a mantener una excelente experiencia del usuario.</span><span class="sxs-lookup"><span data-stu-id="3b64d-144">Managed availability that helps you maintain a great user experience.</span></span>
    
- <span data-ttu-id="3b64d-145">Aproveche la infraestructura existente de hardware y almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="3b64d-145">Leverage existing hardware and storage infrastructure.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="3b64d-146">Exchange hospedado por el proveedor</span><span class="sxs-lookup"><span data-stu-id="3b64d-146">Provider-Hosted Exchange</span></span>

<span data-ttu-id="3b64d-147">Puede subcontratar su carga de trabajo de Exchange Server a un proveedor de soluciones de Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="3b64d-147">You can outsource your Exchange Server workload to an Exchange Server solutions provider.</span></span>
  
<span data-ttu-id="3b64d-148">El diagrama correspondiente muestra un entorno de Exchange Server que un proveedor se encarga de hacer funcionar y mantener.</span><span class="sxs-lookup"><span data-stu-id="3b64d-148">The accompanying diagram shows an Exchange Server environment that is operated and maintained by a provider.</span></span>
  
<span data-ttu-id="3b64d-149">Descripción de las características y funcionalidades:</span><span class="sxs-lookup"><span data-stu-id="3b64d-149">Description of features and functionality:</span></span>
  
- <span data-ttu-id="3b64d-150">El proveedor controla el funcionamiento de los servidores y el software de servidor.</span><span class="sxs-lookup"><span data-stu-id="3b64d-150">The operation of servers and server software is handled by your provider.</span></span>
    
- <span data-ttu-id="3b64d-151">Se delegan al proveedor la planeación, la modificación de tamaño, el escalado y el mantenimiento de la infraestructura de Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="3b64d-151">Planning, sizing, scaling, and maintenance of the Exchange Server infrastructure are delegated to your provider.</span></span>
    
- <span data-ttu-id="3b64d-152">El proveedor controla el mantenimiento de servicio.</span><span class="sxs-lookup"><span data-stu-id="3b64d-152">Service maintenance is handled by your provider.</span></span>
    
- <span data-ttu-id="3b64d-153">El conjunto de características de Exchange está limitado a la versión de software que el proveedor implementa.</span><span class="sxs-lookup"><span data-stu-id="3b64d-153">The Exchange feature set is limited to the software version deployed by your provider.</span></span>
    
### <a name="benefits-of-implementing-each-deployment-option"></a><span data-ttu-id="3b64d-154">Ventajas de la implementación de cada opción de implementación</span><span class="sxs-lookup"><span data-stu-id="3b64d-154">Benefits of implementing each deployment option</span></span>

#### <a name="exchange-online-office-365"></a><span data-ttu-id="3b64d-155">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="3b64d-155">Exchange Online (Office 365)</span></span>

<span data-ttu-id="3b64d-156">Esta opción de implementación es la mejor para:</span><span class="sxs-lookup"><span data-stu-id="3b64d-156">This deployment option is best for:</span></span>
  
- <span data-ttu-id="3b64d-157">Organizaciones que buscan reducir costes de operaciones para implementaciones de Exchange local.</span><span class="sxs-lookup"><span data-stu-id="3b64d-157">Organizations looking to reduce operations costs for on-premises Exchange deployments.</span></span>
    
- <span data-ttu-id="3b64d-158">Organizaciones que planean aprovechar otras ofertas de Office 365, como SharePoint Online y Lync Online.</span><span class="sxs-lookup"><span data-stu-id="3b64d-158">Organizations that plan to leverage other Office 365 offerings, such as SharePoint Online and Lync Online.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="3b64d-159">Exchange Hybrid</span><span class="sxs-lookup"><span data-stu-id="3b64d-159">Exchange Hybrid</span></span>

<span data-ttu-id="3b64d-160">Esta opción de implementación es la mejor para:</span><span class="sxs-lookup"><span data-stu-id="3b64d-160">This deployment option is best for:</span></span>
  
- <span data-ttu-id="3b64d-161">Facilitar una migración de Exchange local a Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="3b64d-161">Facilitating a migration from Exchange on-premises to Exchange Online.</span></span>
    
- <span data-ttu-id="3b64d-162">Soporte de sitios remotos sin invertir en infraestructura de oficinas de sucursales.</span><span class="sxs-lookup"><span data-stu-id="3b64d-162">Supporting remote sites without investing in branch office infrastructure.</span></span>
    
- <span data-ttu-id="3b64d-163">Multinacionales con filiales que requieren datos que residan de forma local.</span><span class="sxs-lookup"><span data-stu-id="3b64d-163">Multinational corporations with subsidiaries that require data to reside on-premises.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="3b64d-164">Exchange Server local</span><span class="sxs-lookup"><span data-stu-id="3b64d-164">Exchange Server on-premises</span></span>

<span data-ttu-id="3b64d-165">Esta opción de implementación es la mejor para:</span><span class="sxs-lookup"><span data-stu-id="3b64d-165">This deployment option is best for:</span></span>
  
- <span data-ttu-id="3b64d-166">Soluciones muy personalizadas.</span><span class="sxs-lookup"><span data-stu-id="3b64d-166">Highly customized solutions.</span></span>
    
- <span data-ttu-id="3b64d-167">Soluciones heredadas con componentes de terceros que dependen de hardware y software que no son compatibles con Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="3b64d-167">Legacy solutions with third-party components that depend on hardware and software that are not supported by Exchange Online.</span></span>
    
- <span data-ttu-id="3b64d-168">Organizaciones sujetas a regulaciones de datos gubernamentales que exigen que los datos residan de forma local.</span><span class="sxs-lookup"><span data-stu-id="3b64d-168">Organizations subject to data governance regulations that require data to reside on-premises.</span></span>
    
- <span data-ttu-id="3b64d-169">Organizaciones que desean conservar el control de toda la plataforma y solución.</span><span class="sxs-lookup"><span data-stu-id="3b64d-169">Organizations that wish to retain control of the entire platform and solution.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="3b64d-170">Exchange hospedado por el proveedor</span><span class="sxs-lookup"><span data-stu-id="3b64d-170">Provider-Hosted Exchange</span></span>

<span data-ttu-id="3b64d-171">Esta opción de implementación es la mejor para:</span><span class="sxs-lookup"><span data-stu-id="3b64d-171">This deployment option is best for:</span></span>
  
- <span data-ttu-id="3b64d-172">Organizaciones que necesitan funcionalidad de Exchange Server, pero desean subcontratar la implementación y el mantenimiento.</span><span class="sxs-lookup"><span data-stu-id="3b64d-172">Organizations that need Exchange Server functionality, but want to outsource its deployment and maintenance.</span></span>
    
- <span data-ttu-id="3b64d-173">Organizaciones que necesitan opciones de soporte personalizado.</span><span class="sxs-lookup"><span data-stu-id="3b64d-173">Organizations that need personalized support options.</span></span>
    
- <span data-ttu-id="3b64d-174">Soluciones e integración personalizadas con aplicaciones personalizadas que el proveedor ofrece.</span><span class="sxs-lookup"><span data-stu-id="3b64d-174">Customized solutions and integration with custom applications offered by the provider.</span></span>
    
- <span data-ttu-id="3b64d-175">Soluciones heredadas con componentes de terceros que dependen de hardware y software que no son compatibles con Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="3b64d-175">Legacy solutions with third-party components that depend on hardware and software that are not supported by Exchange Online.</span></span>
    
### <a name="license-requirements"></a><span data-ttu-id="3b64d-176">Requisitos de licencia</span><span class="sxs-lookup"><span data-stu-id="3b64d-176">License requirements</span></span>

<span data-ttu-id="3b64d-177">La siguiente tabla detalla los requisitos de licencia para cada opción de implementación.</span><span class="sxs-lookup"><span data-stu-id="3b64d-177">The following table details the license requirements for each deployment option.</span></span>
  
|<span data-ttu-id="3b64d-178">**Opción de implementación**</span><span class="sxs-lookup"><span data-stu-id="3b64d-178">**Deployment option**</span></span>|<span data-ttu-id="3b64d-179">**Requisitos de licencia**</span><span class="sxs-lookup"><span data-stu-id="3b64d-179">**License requirements**</span></span>|
|:-----|:-----|
|<span data-ttu-id="3b64d-180">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="3b64d-180">Exchange Online (Office 365)</span></span>  <br/> |<span data-ttu-id="3b64d-181">Modelo de suscripción</span><span class="sxs-lookup"><span data-stu-id="3b64d-181">Subscription model</span></span>  <br/> |
|<span data-ttu-id="3b64d-182">Exchange Hybrid</span><span class="sxs-lookup"><span data-stu-id="3b64d-182">Exchange Hybrid</span></span>  <br/> | <span data-ttu-id="3b64d-183">Office 365: Modelo de suscripción</span><span class="sxs-lookup"><span data-stu-id="3b64d-183">Office 365 - Subscription model</span></span> <br/>  <span data-ttu-id="3b64d-184">Local: Se aplican todas las licencias locales (revise las licencias para Exchange Server local)</span><span class="sxs-lookup"><span data-stu-id="3b64d-184">On-premises - All on-premises licenses apply (review licenses for Exchanges Server on-premises)</span></span> <br/>  <span data-ttu-id="3b64d-185">Licencia de servidor híbrido\*</span><span class="sxs-lookup"><span data-stu-id="3b64d-185">Hybrid server license\*</span></span> <br/> |
|<span data-ttu-id="3b64d-186">Exchange Server local</span><span class="sxs-lookup"><span data-stu-id="3b64d-186">Exchange Server on-premises</span></span>  <br/> | <span data-ttu-id="3b64d-187">Sistema operativo del servidor</span><span class="sxs-lookup"><span data-stu-id="3b64d-187">Server Operating System</span></span> <br/>  <span data-ttu-id="3b64d-188">Licencia de Exchange 2013 Server</span><span class="sxs-lookup"><span data-stu-id="3b64d-188">Exchange 2013 Server License</span></span> <br/>  <span data-ttu-id="3b64d-189">Licencia de acceso de cliente de Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="3b64d-189">Exchange 2013 Client Access License</span></span> <br/> |
|<span data-ttu-id="3b64d-190">Exchange hospedado por el proveedor</span><span class="sxs-lookup"><span data-stu-id="3b64d-190">Provider-Hosted Exchange</span></span>  <br/> |<span data-ttu-id="3b64d-191">Los costes se basan en el acuerdo con el proveedor</span><span class="sxs-lookup"><span data-stu-id="3b64d-191">Costs are based on the agreement with the provider</span></span>  <br/> |
   
### <a name="architecture-tasks"></a><span data-ttu-id="3b64d-192">Tareas de arquitectura</span><span class="sxs-lookup"><span data-stu-id="3b64d-192">Architecture tasks</span></span>

<span data-ttu-id="3b64d-193">Esta sección muestra las tareas de arquitectura para cada opción de implementación.</span><span class="sxs-lookup"><span data-stu-id="3b64d-193">This section lists the architectural tasks for each deployment option.</span></span>
  
#### <a name="exchange-online-office-365"></a><span data-ttu-id="3b64d-194">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="3b64d-194">Exchange Online (Office 365)</span></span>

- <span data-ttu-id="3b64d-195">Planee y diseñe la sincronización de directorios.</span><span class="sxs-lookup"><span data-stu-id="3b64d-195">Plan and design the directory synchronization.</span></span>
    
- <span data-ttu-id="3b64d-196">Garantice la capacidad de red y conectividad mediante firewalls, servidores proxy, puertas de enlace y vínculos por WAN.</span><span class="sxs-lookup"><span data-stu-id="3b64d-196">Ensure network capacity and connectivity through firewalls, proxy servers, gateways, and across WAN links.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="3b64d-197">Exchange Hybrid</span><span class="sxs-lookup"><span data-stu-id="3b64d-197">Exchange Hybrid</span></span>

<span data-ttu-id="3b64d-198">Además de las tareas de arquitectura para los entornos de Office 365 y locales:</span><span class="sxs-lookup"><span data-stu-id="3b64d-198">In addition to the architecture tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="3b64d-199">Decida si va a proporcionar una experiencia de inicio de sesión único.</span><span class="sxs-lookup"><span data-stu-id="3b64d-199">Decide whether to provide a single-sign on experience.</span></span>
    
- <span data-ttu-id="3b64d-200">Decida si va a enrutar el correo entrante de Internet a través de una organización local o a través de Exchange Online Protection.</span><span class="sxs-lookup"><span data-stu-id="3b64d-200">Decide whether to route inbound Internet mail through an on-premises organization or through Exchange Online Protection.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="3b64d-201">Exchange Server local</span><span class="sxs-lookup"><span data-stu-id="3b64d-201">Exchange Server on-premises</span></span>

- <span data-ttu-id="3b64d-202">Diseñe la topología de Exchange.</span><span class="sxs-lookup"><span data-stu-id="3b64d-202">Design the Exchange topology.</span></span>
    
- <span data-ttu-id="3b64d-203">Planee la capacidad para hardware de servidor.</span><span class="sxs-lookup"><span data-stu-id="3b64d-203">Plan the capacity for server hardware.</span></span>
    
- <span data-ttu-id="3b64d-204">Diseñe la topología de enrutamiento de mensajes.</span><span class="sxs-lookup"><span data-stu-id="3b64d-204">Design the message routing topology.</span></span>
    
- <span data-ttu-id="3b64d-205">Diseñe equilibrio de carga para servidores de acceso de cliente.</span><span class="sxs-lookup"><span data-stu-id="3b64d-205">Design load balancing for Client Access servers.</span></span>
    
- <span data-ttu-id="3b64d-206">Planee una alta disponibilidad con grupos de disponibilidad de bases de datos.</span><span class="sxs-lookup"><span data-stu-id="3b64d-206">Plan for high availability using database availability groups.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="3b64d-207">Exchange hospedado por el proveedor</span><span class="sxs-lookup"><span data-stu-id="3b64d-207">Provider-Hosted Exchange</span></span>

<span data-ttu-id="3b64d-208">Asegúrese de que la capacidad de red y disponibilidad mediante firewalls, servidores proxy, puertas de enlace y vínculos por WAN estén disponibles para su proveedor.</span><span class="sxs-lookup"><span data-stu-id="3b64d-208">Ensure that the network capacity and availability through firewalls, proxy servers, gateways, and across WAN links are available to your provider.</span></span>
  
### <a name="it-pro-responsibilities"></a><span data-ttu-id="3b64d-209">Responsabilidades del profesional de TI</span><span class="sxs-lookup"><span data-stu-id="3b64d-209">IT Pro responsibilities</span></span>

<span data-ttu-id="3b64d-210">Esta sección muestra las responsabilidades del profesional de TI para cada opción de implementación.</span><span class="sxs-lookup"><span data-stu-id="3b64d-210">This section lists the IT Pro responsibilities for each deployment option.</span></span>
  
#### <a name="exchange-online-office-365"></a><span data-ttu-id="3b64d-211">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="3b64d-211">Exchange Online (Office 365)</span></span>

- <span data-ttu-id="3b64d-212">Implemente el plan de sincronización de directorios.</span><span class="sxs-lookup"><span data-stu-id="3b64d-212">Implement the directory synchronization plan.</span></span>
    
- <span data-ttu-id="3b64d-213">Planee e implemente enrutamiento y registros DNS internos y externos.</span><span class="sxs-lookup"><span data-stu-id="3b64d-213">Plan and implement internal and external DNS records and routing.</span></span>
    
- <span data-ttu-id="3b64d-214">Configure el servidor proxy o firewall para los requisitos de direcciones URL e IP de Office 365.</span><span class="sxs-lookup"><span data-stu-id="3b64d-214">Configure the proxy server or firewall for the Office 365 IP address and URL requirements.</span></span>
    
- <span data-ttu-id="3b64d-215">Administre las cuentas de usuario y la configuración de Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="3b64d-215">Administer the user accounts and the Exchange Online settings.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="3b64d-216">Exchange Hybrid</span><span class="sxs-lookup"><span data-stu-id="3b64d-216">Exchange Hybrid</span></span>

<span data-ttu-id="3b64d-217">Además de las responsabilidades del profesional de TI para los entornos de Office 365 y locales:</span><span class="sxs-lookup"><span data-stu-id="3b64d-217">In addition to the IT Pro responsibilities for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="3b64d-218">Configure los Servicios de federación de Active Directory (AD FS) para inicio de sesión único (si lo desea).</span><span class="sxs-lookup"><span data-stu-id="3b64d-218">Configure Active Directory Federation Services (AD FS) for single-sign on (if desired).</span></span>
    
- <span data-ttu-id="3b64d-219">Configure certificados de Exchange para proteger las comunicaciones entre servidores de Exchange 2013 y Office 365.</span><span class="sxs-lookup"><span data-stu-id="3b64d-219">Configure Exchange certificates for secure communications between Exchange 2013 servers and Office 365.</span></span>
    
- <span data-ttu-id="3b64d-220">Configure registros DNS para la ruta de correo de Internet entrante que desee.</span><span class="sxs-lookup"><span data-stu-id="3b64d-220">Configure DNS records for the desired inbound Internet mail path.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="3b64d-221">Exchange Server local</span><span class="sxs-lookup"><span data-stu-id="3b64d-221">Exchange Server on-premises</span></span>

- <span data-ttu-id="3b64d-222">Configure los certificados necesarios para los servicios de Exchange.</span><span class="sxs-lookup"><span data-stu-id="3b64d-222">Configure the necessary certificates for Exchange services.</span></span>
    
- <span data-ttu-id="3b64d-223">Aprovisione los servidores.</span><span class="sxs-lookup"><span data-stu-id="3b64d-223">Provision the servers.</span></span>
    
- <span data-ttu-id="3b64d-224">Implemente la topología de enrutamiento de mensajes de Exchange.</span><span class="sxs-lookup"><span data-stu-id="3b64d-224">Implement the Exchange message routing topology.</span></span>
    
- <span data-ttu-id="3b64d-225">Implemente grupos de disponibilidad de bases de datos.</span><span class="sxs-lookup"><span data-stu-id="3b64d-225">Implement database availability groups.</span></span>
    
- <span data-ttu-id="3b64d-226">Actualice y mantenga servidores de Exchange.</span><span class="sxs-lookup"><span data-stu-id="3b64d-226">Update and maintain Exchange servers.</span></span>
    
- <span data-ttu-id="3b64d-227">En función de la utilización, agregue o quite servidores según sea necesario.</span><span class="sxs-lookup"><span data-stu-id="3b64d-227">Depending on utilization, add or remove servers as needed.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="3b64d-228">Exchange hospedado por el proveedor</span><span class="sxs-lookup"><span data-stu-id="3b64d-228">Provider-Hosted Exchange</span></span>

<span data-ttu-id="3b64d-229">Las responsabilidades del proveedor incluyen:</span><span class="sxs-lookup"><span data-stu-id="3b64d-229">The provider's responsibilities include:</span></span>
  
- <span data-ttu-id="3b64d-230">Mantenimiento del sistema y el servicio.</span><span class="sxs-lookup"><span data-stu-id="3b64d-230">System and service maintenance.</span></span>
    
- <span data-ttu-id="3b64d-231">Lanzamientos de características.</span><span class="sxs-lookup"><span data-stu-id="3b64d-231">Feature rollouts.</span></span>
    
- <span data-ttu-id="3b64d-232">Recuperación ante desastres y protección de datos.</span><span class="sxs-lookup"><span data-stu-id="3b64d-232">Data protection and disaster recovery.</span></span>
    
<span data-ttu-id="3b64d-233">Las responsabilidades del personal de TI de la organización incluyen crear y administrar cuentas de usuarios.</span><span class="sxs-lookup"><span data-stu-id="3b64d-233">The IT staff's responsibilities in your organization include creating and managing user accounts.</span></span>
  
#### <a name="more-information"></a><span data-ttu-id="3b64d-234">Más información</span><span class="sxs-lookup"><span data-stu-id="3b64d-234">More information</span></span>

<span data-ttu-id="3b64d-235">Para obtener más información sobre Exchange Online (Office 365), consulte:</span><span class="sxs-lookup"><span data-stu-id="3b64d-235">To learn more about Exchange Online (Office 365), see the following:</span></span>
  
- [<span data-ttu-id="3b64d-236">Descripción de servicio de Exchange Online</span><span class="sxs-lookup"><span data-stu-id="3b64d-236">Exchange Online service description</span></span>](https://aka.ms/EXOSD)
    
- [<span data-ttu-id="3b64d-237">Biblioteca de Exchange Online en TechNet</span><span class="sxs-lookup"><span data-stu-id="3b64d-237">Exchange Online library on TechNet</span></span>](https://aka.ms/EXOTN)
    
- [<span data-ttu-id="3b64d-238">Portal de Exchange Online</span><span class="sxs-lookup"><span data-stu-id="3b64d-238">Exchange Online portal</span></span>](https://aka.ms/EXO)
    
<span data-ttu-id="3b64d-239">Para obtener más información sobre Exchange Hybrid, consulte:</span><span class="sxs-lookup"><span data-stu-id="3b64d-239">To learn more about Exchange Hybrid, see the following:</span></span>
  
- <span data-ttu-id="3b64d-p104">[Implementaciones híbridas de Exchange 2013 ](https://aka.ms/ExchangeHybrid). Tenga en cuenta que la licencia del servidor híbrido solo se requiere para los siguientes escenarios: organización de Exchange 2010 con servidor híbrido Exchange 2013 y organización de Exchange 2007 con servidor híbrido Exchange 2013 o Exchange 2010.</span><span class="sxs-lookup"><span data-stu-id="3b64d-p104">[Exchange 2013 hybrid deployments](https://aka.ms/ExchangeHybrid). You should note that the Hybrid server license is only required for the following scenarios: Exchange 2010 organization with Exchange 2013 hybrid server and Exchange 2007 organization with Exchange 2013 or Exchange 2010 hybrid server.</span></span>
    
- [<span data-ttu-id="3b64d-242">Inicio de sesión de Office 365</span><span class="sxs-lookup"><span data-stu-id="3b64d-242">Office 365 Sign in</span></span>](https://aka.ms/HybridKey)
    
<span data-ttu-id="3b64d-243">Para obtener más información sobre Exchange Server local, consulte:</span><span class="sxs-lookup"><span data-stu-id="3b64d-243">To learn more about Exchange Server on-premises, see the following:</span></span>
  
- [<span data-ttu-id="3b64d-244">Biblioteca de Exchange Server 2013 en TechNet</span><span class="sxs-lookup"><span data-stu-id="3b64d-244">Exchange Server 2013 library on TechNet</span></span>](https://aka.ms/Ex2013TN)
    
- [<span data-ttu-id="3b64d-245">Portal de Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="3b64d-245">Exchange Server 2013 portal</span></span>](https://aka.ms/Exchange2013)
    
- [<span data-ttu-id="3b64d-246">Arquitectura de Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="3b64d-246">Exchange Server 2013 architecture</span></span>](https://aka.ms/Ex2013SP1ArchPoster)
    
<span data-ttu-id="3b64d-247">Para obtener más información sobre Exchange hospedado por el proveedor, consulte:</span><span class="sxs-lookup"><span data-stu-id="3b64d-247">To learn more about Provider-Hosted Exchange, see the following:</span></span>
  
[<span data-ttu-id="3b64d-248">Guía y soluciones de varios inquilinos y hospedaje de Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="3b64d-248">Exchange Server 2013 hosting and multi-tenancy solutions and guidance</span></span>](https://aka.ms/Ex2013Hosting)
  
## <a name="descriptions-of-three-new-or-updated-features-in-exchange-2013"></a><span data-ttu-id="3b64d-249">Descripciones de tres características nuevas o actualizadas en Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="3b64d-249">Descriptions of three new or updated features in Exchange 2013</span></span>

### <a name="exchange-online-protection"></a><span data-ttu-id="3b64d-250">Exchange Online Protection</span><span class="sxs-lookup"><span data-stu-id="3b64d-250">Exchange Online Protection</span></span>

<span data-ttu-id="3b64d-p105">Exchange Online Protection (EOP) proporciona protección de correo no deseado y contra malware para cualquier implementación mediante una capa de características de protección que se implementan en una red global de centros de datos. Esto ayuda a simplificar la administración de los entornos de mensajería. EOP se incluye en las suscripciones de Exchange Online, pero también es adecuado para implementaciones híbridas y locales.</span><span class="sxs-lookup"><span data-stu-id="3b64d-p105">Exchange Online Protection (EOP) provides anti-spam and anti-malware protection for any deployment by providing a layer of protection features that are deployed across a global network of data centers. This helps you to simplify the management of your messaging environments. EOP is included in Exchange Online subscriptions, but you can also leverage it for hybrid and on-premises deployments.</span></span>
  
<span data-ttu-id="3b64d-254">Los diagramas correspondientes muestran implementaciones para Exchange Online, Exchange Hybrid e Exchange local que incluyen la capa EOP en la red global.</span><span class="sxs-lookup"><span data-stu-id="3b64d-254">The accompanying diagrams show deployments for Exchange Online, Exchange Hybrid, and Exchange on-premises that include the EOP layer in the global network.</span></span>
  
### <a name="exchange-server-deployment-assistant"></a><span data-ttu-id="3b64d-255">Asistente para la implementación de Exchange Server</span><span class="sxs-lookup"><span data-stu-id="3b64d-255">Exchange Server Deployment Assistant</span></span>

<span data-ttu-id="3b64d-p106">El Asistente para la implementación de Exchange Server es una herramienta basada en Internet que realiza algunas preguntas sobre el entorno actual, y luego genera una lista de comprobación personalizada y paso a paso para ayudarle a implementar Exchange Server para diferentes tipos de escenarios. Ya sea que migre desde una versión previa de Exchange a Exchange 2013, migre a Exchange Online, o planee una infraestructura híbrida, el Asistente para la implementación de Exchange Server crea una lista de comprobación de implementación personalizada para su escenario.</span><span class="sxs-lookup"><span data-stu-id="3b64d-p106">The Exchange Server Deployment Assistant is a web-based tool that asks you a few questions about your current environment, and then generates a custom step-by-step checklist to help you deploy Exchange Server for different types of scenarios. Whether you are migrating from a previous version of Exchange to Exchange 2013, migrating to Exchange Online, or planning a hybrid infrastructure, the Exchange Server Deployment Assistant creates a customized deployment checklist for your scenario.</span></span>
  
<span data-ttu-id="3b64d-258">La captura de pantalla correspondiente muestra una lista de comprobación de ejemplo creada con el Asistente para la implementación de Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="3b64d-258">The accompanying screenshot shows an example checklist that was created using the Exchange Server Deployment Assistant.</span></span>
  
### <a name="integration-with-lync-and-sharepoint"></a><span data-ttu-id="3b64d-259">Integración con Lync y SharePoint</span><span class="sxs-lookup"><span data-stu-id="3b64d-259">Integration with Lync and SharePoint</span></span>

<span data-ttu-id="3b64d-p107">Exchange Server 2013 incluye muchas características que se integran con Lync Server 2013 y SharePoint Server 2013. En conjunto, estos productos ofrecen una amplia variedad de características y mejoran la colaboración en la organización.</span><span class="sxs-lookup"><span data-stu-id="3b64d-p107">Exchange Server 2013 includes many features that integrate with Lync Server 2013 and SharePoint Server 2013. Together, these products offer a rich suite of features and improve collaboration across your organization.</span></span> 
  
<span data-ttu-id="3b64d-262">El diagrama correspondiente muestra el póster de autenticación de servidor a servidor e incluye un vínculo al póster.</span><span class="sxs-lookup"><span data-stu-id="3b64d-262">An accompanying diagram shows the Server-to-Server Authentication poster and includes a link to the poster.</span></span> 
  
- <span data-ttu-id="3b64d-263">Archivado, suspensión y exhibición de documentos electrónicos</span><span class="sxs-lookup"><span data-stu-id="3b64d-263">Archiving, hold and eDiscovery</span></span>
    
- <span data-ttu-id="3b64d-264">Buzones de sitio</span><span class="sxs-lookup"><span data-stu-id="3b64d-264">Site mailboxes</span></span>
    
- <span data-ttu-id="3b64d-265">Almacén de contactos unificado</span><span class="sxs-lookup"><span data-stu-id="3b64d-265">Unified contact store</span></span>
    
- <span data-ttu-id="3b64d-266">Fotos de usuarios en alta resolución</span><span class="sxs-lookup"><span data-stu-id="3b64d-266">High-resolution user photos</span></span>
    
- <span data-ttu-id="3b64d-267">Presencia de Lync en Outlook y Outlook Web App</span><span class="sxs-lookup"><span data-stu-id="3b64d-267">Lync presence in Outlook and Outlook Web App</span></span>
    
- <span data-ttu-id="3b64d-268">Autenticación de servidor en servidor</span><span class="sxs-lookup"><span data-stu-id="3b64d-268">Server-to-server authentication</span></span>
    
- <span data-ttu-id="3b64d-269">Correo de voz</span><span class="sxs-lookup"><span data-stu-id="3b64d-269">Voicemail</span></span>
    
- <span data-ttu-id="3b64d-270">Grabaciones de reuniones</span><span class="sxs-lookup"><span data-stu-id="3b64d-270">Meeting recordings</span></span>
    
- <span data-ttu-id="3b64d-271">Sincronización de tareas de Exchange</span><span class="sxs-lookup"><span data-stu-id="3b64d-271">Exchange task synchronization</span></span>
    
<span data-ttu-id="3b64d-272">El diagrama correspondiente muestra el póster de la arquitectura de Exchange Server 2013 SP1 e incluye un vínculo al póster.</span><span class="sxs-lookup"><span data-stu-id="3b64d-272">An accompanying diagram shows the Exchange Server 2013 SP1 Architecture poster and includes a link to the poster.</span></span>
  

