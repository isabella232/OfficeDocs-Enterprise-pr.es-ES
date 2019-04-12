---
title: Implementar la autenticación federada de alta disponibilidad para Office 365 en Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/06/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150s
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: 34b1ab9c-814c-434d-8fd0-e5a82cd9bff6
description: 'Resumen: Configure la autenticación federada de alta disponibilidad para su suscripción de Office 365 en Microsoft Azure.'
ms.openlocfilehash: 9139019cf53b3a43bcc6d8ebcfbad5d4f7f5506f
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741276"
---
# <a name="deploy-high-availability-federated-authentication-for-office-365-in-azure"></a><span data-ttu-id="43ec1-103">Implementar la autenticación federada de alta disponibilidad para Office 365 en Azure</span><span class="sxs-lookup"><span data-stu-id="43ec1-103">Deploy high availability federated authentication for Office 365 in Azure</span></span>

 <span data-ttu-id="43ec1-104">**Resumen:** Configure la autenticación federada de alta disponibilidad para su suscripción de Office 365 en Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="43ec1-104">**Summary:** Configure high availability federated authentication for your Office 365 subscription in Microsoft Azure.</span></span>
  
<span data-ttu-id="43ec1-105">Este artículo contiene vínculos a las instrucciones detalladas para implementar la autenticación federada de alta disponibilidad para Microsoft Office 365 en los servicios de infraestructura de Azure con estas máquinas virtuales:</span><span class="sxs-lookup"><span data-stu-id="43ec1-105">This article has links to the step-by-step instructions for deploying high availability federated authentication for Microsoft Office 365 in Azure infrastructure services with these virtual machines:</span></span>
  
- <span data-ttu-id="43ec1-106">Dos servidores proxy de aplicación web</span><span class="sxs-lookup"><span data-stu-id="43ec1-106">Two web application proxy servers</span></span>
    
- <span data-ttu-id="43ec1-107">Dos servidores de Servicios de federación de Active Directory (AD FS)</span><span class="sxs-lookup"><span data-stu-id="43ec1-107">Two Active Directory Federation Services (AD FS) servers</span></span>
    
- <span data-ttu-id="43ec1-108">Dos controladores de dominio de réplica</span><span class="sxs-lookup"><span data-stu-id="43ec1-108">Two replica domain controllers</span></span>
    
- <span data-ttu-id="43ec1-109">Un servidor de sincronización de directorios (DirSync) que ejecute Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="43ec1-109">One directory synchronization (DirSync) server running Azure AD Connect</span></span>
    
<span data-ttu-id="43ec1-110">Esta es la configuración, con nombres de marcador de posición para cada servidor.</span><span class="sxs-lookup"><span data-stu-id="43ec1-110">Here is the configuration, with placeholder names for each server.</span></span>
  
**<span data-ttu-id="43ec1-111">Una autenticación federada de alta disponibilidad para Office 365 en Azure</span><span class="sxs-lookup"><span data-stu-id="43ec1-111">A high availability federated authentication for Office 365 infrastructure in Azure</span></span>**

![La configuración final de la infraestructura de la autenticación federada de Office 365 con alta disponibilidad en Azure](media/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
<span data-ttu-id="43ec1-113">Todas las máquinas virtuales forman parte de una única red virtual entre locales de Azure (VNet).</span><span class="sxs-lookup"><span data-stu-id="43ec1-113">All of the virtual machines are in a single cross-premises Azure virtual network (VNet).</span></span> 
  
> [!NOTE]
> <span data-ttu-id="43ec1-p101">La autenticación federada de los usuarios individuales no se basa en los recursos locales. Sin embargo, si la conexión entre locales está disponible, los controladores de dominio de VNet no recibirán actualizaciones de grupos y cuentas de usuario realizados en el entorno de Servicios de dominio de Active Directory (AD DS) local. Para asegurarse de que esto no sucede, puede configurar la alta disponibilidad para la conexión entre locales. Para obtener más información, consulte [Conectividad de red virtual a red virtual y con alta disponibilidad entre locales](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable).</span><span class="sxs-lookup"><span data-stu-id="43ec1-p101">Federated authentication of individual users does not rely on any on-premises resources. However, if the cross-premises connection becomes unavailable, the domain controllers in the VNet will not receive updates to user accounts and groups made in the on-premises Active Directory Domain Services (AD DS). To ensure this does not happen, you can configure high availability for your cross-premises connection. For more information, see [Highly Available Cross-Premises and VNet-to-VNet Connectivity](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span></span>
  
<span data-ttu-id="43ec1-118">Cada par de máquinas virtuales asignado a un rol específico forma parte de su propia subred y de su propio conjunto de disponibilidad.</span><span class="sxs-lookup"><span data-stu-id="43ec1-118">Each pair of virtual machines for a specific role is in its own subnet and availability set.</span></span>
  
> [!NOTE]
> <span data-ttu-id="43ec1-p102">Debido a que esta red virtual está conectada a la red local, la configuración no incluye máquinas virtuales intermedias ni de supervisión en una subred de administración. Para obtener más información, consulte [Running Windows VMs for an N-tier architecture](https://docs.microsoft.com/azure/guidance/guidance-compute-n-tier-vm).</span><span class="sxs-lookup"><span data-stu-id="43ec1-p102">Because this VNet is connected to the on-premises network, this configuration does not include jumpbox or monitoring virtual machines on a management subnet. For more information, see [Running Windows VMs for an N-tier architecture](https://docs.microsoft.com/azure/guidance/guidance-compute-n-tier-vm).</span></span> 
  
<span data-ttu-id="43ec1-p103">El resultado de esta configuración es que tendrá una autenticación federada para todos los usuarios de Office 365, en la que se pueden utilizar las credenciales de Active Directory Domain Services para iniciar sesión en lugar de la cuenta de Office 365. La infraestructura de autenticación federada utiliza un conjunto redundante de servidores que se implementan más fácilmente en servicios de la infraestructura de Azure en lugar de en la red perimetral local.</span><span class="sxs-lookup"><span data-stu-id="43ec1-p103">The result of this configuration is that you will have federated authentication for all of your Office 365 users, in which they can use their Windows Server Active Directory credentials to sign in rather than their Office 365 account. The federated authentication infrastructure uses a redundant set of servers that are more easily deployed in Azure infrastructure services, rather than in your on-premises edge network.</span></span>
  
## <a name="bill-of-materials"></a><span data-ttu-id="43ec1-123">Lista de materiales</span><span class="sxs-lookup"><span data-stu-id="43ec1-123">Bill of materials</span></span>

<span data-ttu-id="43ec1-124">Esta configuración de línea base requiere el siguiente conjunto de componentes y servicios de Azure:</span><span class="sxs-lookup"><span data-stu-id="43ec1-124">This baseline configuration requires the following set of Azure services and components:</span></span>
  
- <span data-ttu-id="43ec1-125">Siete máquinas virtuales</span><span class="sxs-lookup"><span data-stu-id="43ec1-125">Seven virtual machines</span></span>
    
- <span data-ttu-id="43ec1-126">Una red virtual entre locales con cuatro subredes</span><span class="sxs-lookup"><span data-stu-id="43ec1-126">One cross-premises virtual network with four subnets</span></span>
    
- <span data-ttu-id="43ec1-127">Cuatro grupos de recursos</span><span class="sxs-lookup"><span data-stu-id="43ec1-127">Four resource groups</span></span>
    
- <span data-ttu-id="43ec1-128">Tres conjuntos de disponibilidad</span><span class="sxs-lookup"><span data-stu-id="43ec1-128">Three availability sets</span></span>
    
- <span data-ttu-id="43ec1-129">Una suscripción a Azure</span><span class="sxs-lookup"><span data-stu-id="43ec1-129">One Azure subscription</span></span>
    
<span data-ttu-id="43ec1-130">Estas son las máquinas virtuales y sus tamaños predeterminados para esta configuración.</span><span class="sxs-lookup"><span data-stu-id="43ec1-130">Here are the virtual machines and their default sizes for this configuration.</span></span>
  
|**<span data-ttu-id="43ec1-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="43ec1-131">Item</span></span>**|**<span data-ttu-id="43ec1-132">Descripción de la máquina virtual</span><span class="sxs-lookup"><span data-stu-id="43ec1-132">Virtual machine description</span></span>**|**<span data-ttu-id="43ec1-133">Imagen de la galería de Azure</span><span class="sxs-lookup"><span data-stu-id="43ec1-133">Azure gallery image</span></span>**|**<span data-ttu-id="43ec1-134">Tamaño predeterminado</span><span class="sxs-lookup"><span data-stu-id="43ec1-134">Default size</span></span>**|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="43ec1-135">1.</span><span class="sxs-lookup"><span data-stu-id="43ec1-135">1.</span></span>  <br/> |<span data-ttu-id="43ec1-136">Primer controlador de dominio</span><span class="sxs-lookup"><span data-stu-id="43ec1-136">First domain controller</span></span>  <br/> |<span data-ttu-id="43ec1-137">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="43ec1-137">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="43ec1-138">D2</span><span class="sxs-lookup"><span data-stu-id="43ec1-138">D2</span></span>  <br/> |
|<span data-ttu-id="43ec1-139">2.</span><span class="sxs-lookup"><span data-stu-id="43ec1-139">2.</span></span>  <br/> |<span data-ttu-id="43ec1-140">Segundo controlador de dominio</span><span class="sxs-lookup"><span data-stu-id="43ec1-140">Second domain controller</span></span>  <br/> |<span data-ttu-id="43ec1-141">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="43ec1-141">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="43ec1-142">D2</span><span class="sxs-lookup"><span data-stu-id="43ec1-142">D2</span></span>  <br/> |
|<span data-ttu-id="43ec1-143">3.</span><span class="sxs-lookup"><span data-stu-id="43ec1-143">3.</span></span>  <br/> |<span data-ttu-id="43ec1-144">Servidor de Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="43ec1-144">Azure AD Connect server</span></span>  <br/> |<span data-ttu-id="43ec1-145">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="43ec1-145">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="43ec1-146">D2</span><span class="sxs-lookup"><span data-stu-id="43ec1-146">D2</span></span>  <br/> |
|<span data-ttu-id="43ec1-147">4.</span><span class="sxs-lookup"><span data-stu-id="43ec1-147">4.</span></span>  <br/> |<span data-ttu-id="43ec1-148">Primer servidor de AD FS</span><span class="sxs-lookup"><span data-stu-id="43ec1-148">First AD FS server</span></span>  <br/> |<span data-ttu-id="43ec1-149">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="43ec1-149">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="43ec1-150">D2</span><span class="sxs-lookup"><span data-stu-id="43ec1-150">D2</span></span>  <br/> |
|<span data-ttu-id="43ec1-151">5.</span><span class="sxs-lookup"><span data-stu-id="43ec1-151">5.</span></span>  <br/> |<span data-ttu-id="43ec1-152">Segundo servidor de AD FS</span><span class="sxs-lookup"><span data-stu-id="43ec1-152">Second AD FS server</span></span>  <br/> |<span data-ttu-id="43ec1-153">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="43ec1-153">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="43ec1-154">D2</span><span class="sxs-lookup"><span data-stu-id="43ec1-154">D2</span></span>  <br/> |
|<span data-ttu-id="43ec1-155">6.</span><span class="sxs-lookup"><span data-stu-id="43ec1-155">6.</span></span>  <br/> |<span data-ttu-id="43ec1-156">Primer servidor proxy de aplicación web</span><span class="sxs-lookup"><span data-stu-id="43ec1-156">First web application proxy server</span></span>  <br/> |<span data-ttu-id="43ec1-157">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="43ec1-157">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="43ec1-158">D2</span><span class="sxs-lookup"><span data-stu-id="43ec1-158">D2</span></span>  <br/> |
|<span data-ttu-id="43ec1-159">7.</span><span class="sxs-lookup"><span data-stu-id="43ec1-159">7.</span></span>  <br/> |<span data-ttu-id="43ec1-160">Segundo servidor proxy de aplicación web</span><span class="sxs-lookup"><span data-stu-id="43ec1-160">Second web application proxy server</span></span>  <br/> |<span data-ttu-id="43ec1-161">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="43ec1-161">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="43ec1-162">D2</span><span class="sxs-lookup"><span data-stu-id="43ec1-162">D2</span></span>  <br/> |
   
<span data-ttu-id="43ec1-163">Para calcular los costos estimados para esta configuración, consulte la [Calculadora de precios de Azure](https://azure.microsoft.com/pricing/calculator/).</span><span class="sxs-lookup"><span data-stu-id="43ec1-163">To compute the estimated costs for this configuration, see the [Azure pricing calculator](https://azure.microsoft.com/pricing/calculator/)</span></span>
  
## <a name="phases-of-deployment"></a><span data-ttu-id="43ec1-164">Fases de implementación</span><span class="sxs-lookup"><span data-stu-id="43ec1-164">Phases of deployment</span></span>

<span data-ttu-id="43ec1-165">Implementará esta carga de trabajo en las fases siguientes:</span><span class="sxs-lookup"><span data-stu-id="43ec1-165">You deploy this workload in the following phases:</span></span>
  
- <span data-ttu-id="43ec1-p104">[Fase 1: Configurar Azure](high-availability-federated-authentication-phase-1-configure-azure.md). Creación de grupos de recursos, cuentas de almacenamiento, conjuntos de disponibilidad y una red virtual entre locales.</span><span class="sxs-lookup"><span data-stu-id="43ec1-p104">[Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md). Create resource groups, storage accounts, availability sets, and a cross-premises virtual network.</span></span>
    
- <span data-ttu-id="43ec1-p105">[Fase 2: Configurar controladores de dominio](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Creación y configuración de controladores de dominio de réplica para Servicios de dominio de Active Directory (AD DS) y el servidor de DirSync.</span><span class="sxs-lookup"><span data-stu-id="43ec1-p105">[Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Create and configure replica Active Directory Domain Services (AD DS) domain controllers and the DirSync server.</span></span>
    
- <span data-ttu-id="43ec1-p106">[Fase 3: Configurar servidores de AD FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Creación y configuración de los dos servidores de AD FS.</span><span class="sxs-lookup"><span data-stu-id="43ec1-p106">[Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Create and configure the two AD FS servers.</span></span>
    
- <span data-ttu-id="43ec1-p107">[Fase 4: Configurar los servidores proxy de aplicación web](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Creación y configuración de los dos servidores proxy de aplicación web.</span><span class="sxs-lookup"><span data-stu-id="43ec1-p107">[Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Create and configure the two web application proxy servers.</span></span>
    
- <span data-ttu-id="43ec1-p108">[Fase 5: Configurar la autenticación federada para Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Configuración de la autenticación federada para su suscripción de Office 365.</span><span class="sxs-lookup"><span data-stu-id="43ec1-p108">[Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Configure federated authentication for your Office 365 subscription.</span></span>
    
<span data-ttu-id="43ec1-p109">En estos artículos, se proporciona una guía preceptiva dividida en fases para una arquitectura predefinida. Su objetivo es crear una autenticación federada de alta disponibilidad funcional para Office 365 en servicios de infraestructura de Azure. Tenga en cuenta lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="43ec1-p109">These articles provide a prescriptive, phase-by-phase guide for a predefined architecture to create a functional, high availability federated authentication for Office 365 in Azure infrastructure services. Keep the following in mind:</span></span>
  
- <span data-ttu-id="43ec1-178">Si es un experimentado implementador de AD FS, no dude en adaptar las instrucciones que se detallan en las fases 3 y 4, así como en crear el conjunto de servidores que mejor se adapte a sus necesidades. </span><span class="sxs-lookup"><span data-stu-id="43ec1-178">If you are an experienced AD FS implementer, feel free to adapt the instructions in phases 3 and 4 and build the set of servers that best suits your needs.</span></span>
    
- <span data-ttu-id="43ec1-179">Si ya tiene una implementación existente de nube híbrida de Azure con una red virtual entre locales existente, no dude en adaptar u omitir las instrucciones que aparecen en las fases 1 y 2 y colocar los servidores proxy de aplicación web y AD FS en las subredes adecuadas.</span><span class="sxs-lookup"><span data-stu-id="43ec1-179">If you already have an existing Azure hybrid cloud deployment with an existing cross-premises virtual network, feel free to adapt or skip the instructions in phases 1 and 2 and place the AD FS and web application proxy servers on the appropriate subnets.</span></span>
    
<span data-ttu-id="43ec1-180">Para crear un entorno de prueba o desarrollo o bien una prueba de concepto de esta configuración, consulte [Identidad federada para el entorno de desarrollo y pruebas de Office 365](federated-identity-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="43ec1-180">To build a dev/test environment or a proof-of-concept of this configuration, see [Federated identity for your Office 365 dev/test environment](federated-identity-for-your-office-365-dev-test-environment.md).</span></span>
  
## <a name="next-step"></a><span data-ttu-id="43ec1-181">Paso siguiente</span><span class="sxs-lookup"><span data-stu-id="43ec1-181">Next step</span></span>

<span data-ttu-id="43ec1-182">Inicie la configuración de esta carga de trabajo con [Fase 1 de la autenticación federada de alta disponibilidad: Configurar Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span><span class="sxs-lookup"><span data-stu-id="43ec1-182">Start the configuration of this workload with [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span> 
  
<!--
> [!TIP]
> For a set of files to more quickly deploy your high availability federated authentication for Office 365 in Azure, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664). 
--> 

