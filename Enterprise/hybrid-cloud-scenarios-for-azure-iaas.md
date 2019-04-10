---
title: Escenarios de nube híbrida para Azure IaaS
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 978f2b76-5aba-4e11-9434-f0efda987be1
description: 'Resumen: comprenda la arquitectura y los escenarios híbridos de las ofertas de la nube basadas en la infraestructura como servicio (IaaS) de Microsoft en Azure.'
ms.openlocfilehash: d3f4b4ccbc9dbfa54e6f1d0988624aeb71f27106
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741366"
---
# <a name="hybrid-cloud-scenarios-for-azure-iaas"></a><span data-ttu-id="c2697-103">Escenarios de nube híbrida para Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="c2697-103">Hybrid cloud scenarios for Azure IaaS</span></span>

 <span data-ttu-id="c2697-104">**Resumen:** Comprenda la arquitectura y los escenarios híbridos de las ofertas de la nube basadas en infraestructura como servicio (IaaS) de Microsoft en Azure.</span><span class="sxs-lookup"><span data-stu-id="c2697-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's Infrastructure as a Service (IaaS)-based cloud offerings in Azure.</span></span>
  
<span data-ttu-id="c2697-105">Extienda su infraestructura informática y de identidad local a la nube al hospedar las cargas de trabajo de ti que se ejecutan en redes virtuales (Vnet) de Azure entre locales.</span><span class="sxs-lookup"><span data-stu-id="c2697-105">Extend your on-premises computing and identity infrastructure into the cloud by hosting IT workloads running in cross-premises Azure virtual networks (VNets).</span></span> 
  
## <a name="azure-iaas-hybrid-scenario-architecture"></a><span data-ttu-id="c2697-106">Arquitectura de escenario híbrido de IaaS de Azure</span><span class="sxs-lookup"><span data-stu-id="c2697-106">Azure IaaS hybrid scenario architecture</span></span>

<span data-ttu-id="c2697-107">En la figura 1 se muestra la arquitectura de escenarios híbridos basados en IaaS de Microsoft en Azure.</span><span class="sxs-lookup"><span data-stu-id="c2697-107">Figure 1 shows the architecture of Microsoft IaaS-based hybrid scenarios in Azure.</span></span>
  
**<span data-ttu-id="c2697-108">Figura 1: escenarios híbridos basados en IaaS de Microsoft en Azure</span><span class="sxs-lookup"><span data-stu-id="c2697-108">Figure 1: Microsoft IaaS-based hybrid scenarios in Azure</span></span>**

![Escenarios híbridos basados en IaaS de Microsoft en Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS.png)
  
<span data-ttu-id="c2697-110">Para cada capa de la arquitectura:</span><span class="sxs-lookup"><span data-stu-id="c2697-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="c2697-111">Aplicaciones y escenarios</span><span class="sxs-lookup"><span data-stu-id="c2697-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="c2697-112">Una carga de trabajo de ti suele ser una aplicación de alta disponibilidad y varios niveles formada por máquinas virtuales (VM) de Azure.</span><span class="sxs-lookup"><span data-stu-id="c2697-112">An IT workload is typically a multi-tier, highly-available application composed of Azure virtual machines (VMs).</span></span>
    
- <span data-ttu-id="c2697-113">Identidad</span><span class="sxs-lookup"><span data-stu-id="c2697-113">Identity</span></span>
    
    <span data-ttu-id="c2697-114">Agregue servidores de identidad, como controladores de dominio de servicios de dominio de Active Directory (AD DS), al conjunto de servidores que se ejecutan en redes virtuales de Azure para la autenticación local.</span><span class="sxs-lookup"><span data-stu-id="c2697-114">Add identity servers, such as Active Directory Domain Services (AD DS) domain controllers, to the set of servers running in Azure VNets for local authentication.</span></span>
    
- <span data-ttu-id="c2697-115">Red</span><span class="sxs-lookup"><span data-stu-id="c2697-115">Network</span></span>
    
    <span data-ttu-id="c2697-116">Use una conexión VPN de sitio a sitio a través de Internet o una conexión de ExpressRoute con emparejamiento privado a IaaS de Azure.</span><span class="sxs-lookup"><span data-stu-id="c2697-116">Use either a site-to-site VPN connection over the Internet or an ExpressRoute connection with private peering to Azure IaaS.</span></span>
    
- <span data-ttu-id="c2697-117">Local</span><span class="sxs-lookup"><span data-stu-id="c2697-117">On-premises</span></span>
    
    <span data-ttu-id="c2697-118">Contiene los servidores de identidad que se sincronizan con los servidores de identidades que se ejecutan en Azure.</span><span class="sxs-lookup"><span data-stu-id="c2697-118">Contains identity servers that are synchronized with the identity servers running in Azure.</span></span> <span data-ttu-id="c2697-119">También puede contener recursos a los que pueden tener acceso las máquinas virtuales que se ejecutan en Azure, como la infraestructura de administración de sistemas y almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="c2697-119">Can also contain resources that VMs running in Azure can access, such as storage and systems management infrastructure.</span></span>
    
## <a name="directory-synchronization-server-for-office-365"></a><span data-ttu-id="c2697-120">Servidor de sincronización de directorios para Office 365</span><span class="sxs-lookup"><span data-stu-id="c2697-120">Directory synchronization server for Office 365</span></span>

<span data-ttu-id="c2697-121">Ejecutar el servidor de sincronización de directorios desde una red virtual de Azure, tal como se muestra en la figura 2, es un ejemplo de la ampliación de la infraestructura informática y de identidad a la nube.</span><span class="sxs-lookup"><span data-stu-id="c2697-121">Running your directory synchronization server from an Azure VNet, as shown in Figure 2, is an example of extending your computing and identity infrastructure to the cloud.</span></span>
  
**<span data-ttu-id="c2697-122">Figura 2: servidor de sincronización de directorios para Office 365 en IaaS de Azure</span><span class="sxs-lookup"><span data-stu-id="c2697-122">Figure 2: Directory synchronization server for Office 365 in Azure IaaS</span></span>**

![Servidor de sincronización de directorios para Office 365 en IaaS de Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-DirSync.png)
  
<span data-ttu-id="c2697-124">En la figura 2, una red local hospeda una infraestructura de AD DS, con un servidor proxy y un enrutador en su periferia.</span><span class="sxs-lookup"><span data-stu-id="c2697-124">In Figure 2, an on-premises network hosts a AD DS infrastructure, with a proxy server and a router at its edge.</span></span> <span data-ttu-id="c2697-125">El enrutador se conecta a una puerta de enlace de Azure en el perímetro de una red virtual de Azure con una conexión de ExpressRoute o VPN de sitio a sitio.</span><span class="sxs-lookup"><span data-stu-id="c2697-125">The router connects to an Azure gateway at the edge of an Azure VNet with a site-to-site VPN or ExpressRoute connection.</span></span> <span data-ttu-id="c2697-126">Dentro de la red virtual, un servidor de sincronización de directorios ejecuta Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="c2697-126">Inside the VNet, a directory synchronization server runs Azure AD Connect.</span></span>
  
<span data-ttu-id="c2697-127">Un servidor de sincronización de directorios para Office 365 sincroniza la lista de cuentas de AD DS con el inquilino de Azure AD de una suscripción a Office 365.</span><span class="sxs-lookup"><span data-stu-id="c2697-127">A directory synchronization server for Office 365 synchronizes the list of accounts in AD DS with the Azure AD tenant of an Office 365 subscription.</span></span>
  
<span data-ttu-id="c2697-128">Un servidor de sincronización de directorios es un servidor basado en Windows que ejecuta Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="c2697-128">A directory synchronization server is a Windows-based server that runs Azure AD Connect.</span></span> <span data-ttu-id="c2697-129">Para un aprovisionamiento más rápido o para reducir el número de servidores locales de la organización, implemente el servidor de sincronización de directorios en una red virtual (VNet) en IaaS de Azure.</span><span class="sxs-lookup"><span data-stu-id="c2697-129">For faster provisioning or to reduce the number of on-premises servers in your organization, deploy your directory synchronization server in a virtual network (VNet) in Azure IaaS.</span></span>
  
<span data-ttu-id="c2697-130">El servidor de sincronización de directorios sondea AD DS en busca de cambios y, a continuación, los sincroniza con la suscripción de Office 365.</span><span class="sxs-lookup"><span data-stu-id="c2697-130">The directory synchronization server polls AD DS for changes and then synchronizes them with the Office 365 subscription.</span></span>
  
<span data-ttu-id="c2697-131">Para obtener más información, vea [deploy Office 365 Directory Synchronization in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span><span class="sxs-lookup"><span data-stu-id="c2697-131">For more information, see [Deploy Office 365 Directory Synchronization in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span></span>
  
## <a name="line-of-business-lob-application"></a><span data-ttu-id="c2697-132">Aplicación de línea de negocio (LOB)</span><span class="sxs-lookup"><span data-stu-id="c2697-132">Line of business (LOB) application</span></span>

<span data-ttu-id="c2697-133">La figura 3 muestra la configuración de una aplicación LOB basada en servidor que se ejecuta en IaaS de Azure.</span><span class="sxs-lookup"><span data-stu-id="c2697-133">Figure 3 shows the configuration of a server-based LOB application running in Azure IaaS.</span></span>
  
**<span data-ttu-id="c2697-134">Figura 3: aplicación LOB en IaaS de Azure</span><span class="sxs-lookup"><span data-stu-id="c2697-134">Figure 3: LOB application in Azure IaaS</span></span>**

![Aplicación de LOB basada en servidor en IaaS de Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-Ex.png)
  
<span data-ttu-id="c2697-136">En la figura 3, una red local hospeda una infraestructura de identidad y usuarios.</span><span class="sxs-lookup"><span data-stu-id="c2697-136">In Figure 3, an on-premises network hosts an identity infrastructure and users.</span></span> <span data-ttu-id="c2697-137">Está conectado a una puerta de enlace de IaaS de Azure con una conexión de ExpressRoute o VPN de sitio a sitio.</span><span class="sxs-lookup"><span data-stu-id="c2697-137">It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection.</span></span> <span data-ttu-id="c2697-138">Azure IaaS hospeda una red virtual que contiene los servidores de la aplicación LOB.</span><span class="sxs-lookup"><span data-stu-id="c2697-138">Azure IaaS hosts a virtual network containing the servers of the LOB application.</span></span>
  
<span data-ttu-id="c2697-139">Puede crear aplicaciones LOB que se ejecuten en máquinas virtuales de Azure, que residen en subredes de una VNet de Azure en un centro de recursos de Azure (también conocido como ubicación).</span><span class="sxs-lookup"><span data-stu-id="c2697-139">You can create LOB applications running on Azure VMs, which reside on subnets of an Azure VNet in an Azure datacenter (also known as a location).</span></span>
  
<span data-ttu-id="c2697-140">Como básicamente está extendiendo su infraestructura local a Azure, debe asignar un espacio de direcciones privadas únicas a sus redes virtuales y actualizar las tablas de enrutamiento local para garantizar la posibilidad de acceso a cada red virtual.</span><span class="sxs-lookup"><span data-stu-id="c2697-140">Because you are essentially extending your on-premises infrastructure to Azure, you must assign unique private address space to your VNets and update your on-premises routing tables to ensure reachability to each VNet.</span></span>
  
<span data-ttu-id="c2697-141">Una vez conectado, estas máquinas virtuales se pueden administrar con conexiones de escritorio remoto o con el software de administración de sistemas, al igual que los servidores locales.</span><span class="sxs-lookup"><span data-stu-id="c2697-141">Once connected, these VMs can be managed with remote desktop connections or with your systems management software, just like your on-premises servers.</span></span>
  
<span data-ttu-id="c2697-142">Al configurar puertos expuestos de forma pública, los usuarios móviles o remotos también pueden tener acceso a estas máquinas virtuales desde Internet.</span><span class="sxs-lookup"><span data-stu-id="c2697-142">By configuring publically-exposed ports, these VMs can also be accessed from the Internet by mobile or remote users.</span></span>
  
<span data-ttu-id="c2697-143">Para obtener una configuración de prueba de concepto, consulte [simulated Cross-premises Virtual Network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span><span class="sxs-lookup"><span data-stu-id="c2697-143">For a proof-of-concept configuration, see [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span></span>
  
<span data-ttu-id="c2697-144">Los atributos de las aplicaciones LOB hospedadas en máquinas virtuales de Azure son los siguientes:</span><span class="sxs-lookup"><span data-stu-id="c2697-144">Attributes of LOB applications hosted on Azure VMs are the following:</span></span>
  
- <span data-ttu-id="c2697-145">Varios niveles</span><span class="sxs-lookup"><span data-stu-id="c2697-145">Multiple tiers</span></span>
    
    <span data-ttu-id="c2697-146">Las aplicaciones de unidad de negocio típicas usan un enfoque en niveles.</span><span class="sxs-lookup"><span data-stu-id="c2697-146">Typical LOB applications use a tiered approach.</span></span> <span data-ttu-id="c2697-147">Los conjuntos de servidores proporcionan identidad, procesamiento de base de datos, procesamiento de aplicaciones y lógicas, y servidores web Front-end para el acceso de empleados o clientes.</span><span class="sxs-lookup"><span data-stu-id="c2697-147">Sets of servers provide identity, database processing, application and logic processing, and front-end web servers for employee or customer access.</span></span> 
    
- <span data-ttu-id="c2697-148">Alta disponibilidad</span><span class="sxs-lookup"><span data-stu-id="c2697-148">High availability</span></span>
    
    <span data-ttu-id="c2697-149">Las aplicaciones LOB típicas proporcionan alta disponibilidad mediante el uso de varios servidores en cada nivel.</span><span class="sxs-lookup"><span data-stu-id="c2697-149">Typical LOB applications provide high availability by using multiple servers in each tier.</span></span> <span data-ttu-id="c2697-150">IaaS de Azure proporciona un SLA de tiempo de actividad del 99,9% para servidores en conjuntos de disponibilidad de Azure.</span><span class="sxs-lookup"><span data-stu-id="c2697-150">Azure IaaS provides a 99.9% uptime SLA for servers in Azure availability sets.</span></span> 
    
- <span data-ttu-id="c2697-151">Distribución de la carga</span><span class="sxs-lookup"><span data-stu-id="c2697-151">Load distribution</span></span>
    
    <span data-ttu-id="c2697-152">Para distribuir la carga de tráfico de red entre varios servidores de un nivel, puede usar un equilibrador de carga de Azure interno o con conexión a Internet.</span><span class="sxs-lookup"><span data-stu-id="c2697-152">To distribute the load of network traffic among multiple servers in a tier, you can use an Internet-facing or internal Azure load balancer.</span></span> <span data-ttu-id="c2697-153">O bien, puede usar un dispositivo del equilibrador de carga dedicado disponible en Azure Marketplace.</span><span class="sxs-lookup"><span data-stu-id="c2697-153">Or, you can use a dedicated load balancer appliance available from the Azure marketplace.</span></span>
    
- <span data-ttu-id="c2697-154">Seguridad</span><span class="sxs-lookup"><span data-stu-id="c2697-154">Security</span></span>
    
    <span data-ttu-id="c2697-155">Para proteger los servidores del tráfico entrante no solicitado de Internet, puede usar grupos de seguridad de red de Azure.</span><span class="sxs-lookup"><span data-stu-id="c2697-155">To protect servers from unsolicited incoming traffic from the Internet, you can use Azure network security groups.</span></span> <span data-ttu-id="c2697-156">Puede definir el tráfico permitido o denegado para una subred o la interfaz de red de una máquina virtual individual.</span><span class="sxs-lookup"><span data-stu-id="c2697-156">You can define allowed or denied traffic for a subnet or the network interface of an individual virtual machine.</span></span>
    
## <a name="sharepoint-server-2016-farm-in-azure"></a><span data-ttu-id="c2697-157">Granja de servidores de SharePoint Server 2016 en Azure</span><span class="sxs-lookup"><span data-stu-id="c2697-157">SharePoint Server 2016 farm in Azure</span></span>

<span data-ttu-id="c2697-158">Un ejemplo de una aplicación LOB de varios niveles y altamente disponible en Azure es una granja de servidores de SharePoint Server 2016, tal como se muestra en la figura 4.</span><span class="sxs-lookup"><span data-stu-id="c2697-158">An example of a multi-tier, highly-available LOB application in Azure is a SharePoint Server 2016 farm, as shown in Figure 4.</span></span>
  
**<span data-ttu-id="c2697-159">Figura 4: una granja de servidores de SharePoint Server 2016 de alta disponibilidad en IaaS de Azure</span><span class="sxs-lookup"><span data-stu-id="c2697-159">Figure 4: A high-availability SharePoint Server 2016 farm in Azure IaaS</span></span>**

![Una granja de servidores de alta disponibilidad de SharePoint Server 2016 en IaaS de Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-SP2016.png)
  
<span data-ttu-id="c2697-161">En la figura 4, una red local hospeda una infraestructura de identidad y usuarios.</span><span class="sxs-lookup"><span data-stu-id="c2697-161">In Figure 4, an on-premises network hosts an identity infrastructure and users.</span></span> <span data-ttu-id="c2697-162">Está conectado a una puerta de enlace de IaaS de Azure con una conexión de ExpressRoute o VPN de sitio a sitio.</span><span class="sxs-lookup"><span data-stu-id="c2697-162">It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection.</span></span> <span data-ttu-id="c2697-163">La red virtual de Azure contiene los servidores de la granja de servidores de SharePoint Server 2016, que incluye niveles independientes para los servidores front-end, los servidores de aplicaciones, el clúster de SQL Server y los controladores de dominio.</span><span class="sxs-lookup"><span data-stu-id="c2697-163">The Azure VNet contains the servers of the SharePoint Server 2016 farm, which includes separate tiers for the front-end servers, the application servers, the SQL Server cluster, and the domain controllers.</span></span>
  
<span data-ttu-id="c2697-164">Esta configuración tiene los siguientes atributos de aplicaciones LOB en Azure:</span><span class="sxs-lookup"><span data-stu-id="c2697-164">This configuration has the following attributes of LOB applications in Azure:</span></span> 
  
- <span data-ttu-id="c2697-165">Niveles</span><span class="sxs-lookup"><span data-stu-id="c2697-165">Tiers</span></span>
    
    <span data-ttu-id="c2697-166">Los servidores que ejecutan diferentes roles dentro de la granja de servidores crean los niveles y cada nivel tiene su propia subred.</span><span class="sxs-lookup"><span data-stu-id="c2697-166">Servers running different roles within the farm create the tiers and each tier has its own subnet.</span></span>
    
- <span data-ttu-id="c2697-167">Alta disponibilidad</span><span class="sxs-lookup"><span data-stu-id="c2697-167">High-availability</span></span>
    
    <span data-ttu-id="c2697-168">Se logra mediante el uso de más de un servidor en cada nivel y la colocación de todos los servidores de un nivel en el mismo conjunto de disponibilidad.</span><span class="sxs-lookup"><span data-stu-id="c2697-168">Achieved by using more than one server in each tier and placing all the servers of a tier in the same availability set.</span></span>
    
- <span data-ttu-id="c2697-169">Distribución de la carga</span><span class="sxs-lookup"><span data-stu-id="c2697-169">Load distribution</span></span>
    
    <span data-ttu-id="c2697-170">Los equilibradores de carga internos de Azure distribuyen el tráfico web de cliente entrante a los servidores front-end (WEB1 y WEB2) y a la dirección IP del agente de escucha del clúster de SQL Server (SQL1, SQL2 y MN1).</span><span class="sxs-lookup"><span data-stu-id="c2697-170">Internal Azure load balancers distribute the incoming client web traffic to the front-end servers (WEB1 and WEB2) and to the listener IP address of the SQL Server cluster (SQL1, SQL2, and MN1).</span></span>
    
- <span data-ttu-id="c2697-171">Seguridad</span><span class="sxs-lookup"><span data-stu-id="c2697-171">Security</span></span>
    
    <span data-ttu-id="c2697-172">Los grupos de seguridad de red para cada subred le permiten configurar el tráfico entrante y saliente permitido.</span><span class="sxs-lookup"><span data-stu-id="c2697-172">Network security groups for each subnet let you to configure allowed inbound and outbound traffic.</span></span>
    
<span data-ttu-id="c2697-173">Siga esta ruta de acceso para una adopción correcta:</span><span class="sxs-lookup"><span data-stu-id="c2697-173">Follow this path for successful adoption:</span></span>
  
1. <span data-ttu-id="c2697-174">Evaluar y experimentar</span><span class="sxs-lookup"><span data-stu-id="c2697-174">Evaluate and experiment</span></span>
    
    <span data-ttu-id="c2697-175">Vea [SharePoint server 2016 en Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure) para conocer las ventajas de ejecutar SharePoint Server 2016 en Azure.</span><span class="sxs-lookup"><span data-stu-id="c2697-175">See [SharePoint Server 2016 in Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure) to understand the benefits of running SharePoint Server 2016 in Azure.</span></span>
    
    <span data-ttu-id="c2697-176">Vea [intranet SharePoint Server 2016 en entorno de prueba y desarrollo de Azure](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment) para crear un entorno de pruebas y desarrollo simulado.</span><span class="sxs-lookup"><span data-stu-id="c2697-176">See [Intranet SharePoint Server 2016 in Azure dev/test environment](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment) to build a simulated dev/test environment</span></span>
    
2. <span data-ttu-id="c2697-177">Diseño</span><span class="sxs-lookup"><span data-stu-id="c2697-177">Design</span></span>
    
    <span data-ttu-id="c2697-178">Vea [Designing a SharePoint Server 2016 Farm in Azure](https://docs.microsoft.com/SharePoint/administration/designing-a-sharepoint-server-2016-farm-in-azure) para recorrer un proceso para determinar el conjunto de elementos de red, cálculo y almacenamiento de la IaaS de Azure para hospedar la granja de servidores y su configuración.</span><span class="sxs-lookup"><span data-stu-id="c2697-178">See [Designing a SharePoint Server 2016 farm in Azure](https://docs.microsoft.com/SharePoint/administration/designing-a-sharepoint-server-2016-farm-in-azure) to step through a process to determine the set of Azure IaaS networking, compute, and storage elements to host your farm and their settings.</span></span>
    
3. <span data-ttu-id="c2697-179">Implementar</span><span class="sxs-lookup"><span data-stu-id="c2697-179">Deploy</span></span>
    
    <span data-ttu-id="c2697-180">Vea [Deploying SharePoint server 2016 with SQL Server alwaysOn Availability Groups in Azure](https://docs.microsoft.com/SharePoint/administration/deploying-sharepoint-server-2016-with-sql-server-alwayson-availability-groups-in) para recorrer la configuración de un extremo a otro de la granja de servidores de alta disponibilidad en cinco fases.</span><span class="sxs-lookup"><span data-stu-id="c2697-180">See [Deploying SharePoint Server 2016 with SQL Server AlwaysOn Availability Groups in Azure](https://docs.microsoft.com/SharePoint/administration/deploying-sharepoint-server-2016-with-sql-server-alwayson-availability-groups-in) to step through the end-to-end configuration of the high-availability farm in five phases.</span></span>
    
## <a name="federated-identity-for-office-365-in-azure"></a><span data-ttu-id="c2697-181">Identidad federada para Office 365 en Azure</span><span class="sxs-lookup"><span data-stu-id="c2697-181">Federated identity for Office 365 in Azure</span></span>

<span data-ttu-id="c2697-182">Otro ejemplo de una aplicación LOB de varios niveles y altamente disponible en Azure es la identidad federada para Office 365.</span><span class="sxs-lookup"><span data-stu-id="c2697-182">Another example of a multi-tier, highly-available LOB application in Azure is federated identity for Office 365.</span></span>
  
**<span data-ttu-id="c2697-183">Figura 5: una infraestructura de identidad federada de alta disponibilidad para Office 365 en IaaS de Azure</span><span class="sxs-lookup"><span data-stu-id="c2697-183">Figure 5: A high-availability federated identity infrastructure for Office 365 in Azure IaaS</span></span>**

![Una infraestructura de autenticación federada de Office 365 de alta disponibilidad en Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-ADFS.png)
  
<span data-ttu-id="c2697-185">En la figura 5, una red local hospeda una infraestructura de identidad y usuarios.</span><span class="sxs-lookup"><span data-stu-id="c2697-185">In Figure 5, an on-premises network hosts an identity infrastructure and users.</span></span> <span data-ttu-id="c2697-186">Está conectado a una puerta de enlace de IaaS de Azure con una conexión de ExpressRoute o VPN de sitio a sitio.</span><span class="sxs-lookup"><span data-stu-id="c2697-186">It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection.</span></span> <span data-ttu-id="c2697-187">La red virtual de Azure contiene servidores proxy Web, servidores de servicios de Federación de Active Directory (AD FS) y controladores de dominio de servicios de dominio de Active Directory (AD DS).</span><span class="sxs-lookup"><span data-stu-id="c2697-187">The Azure VNet contains web proxy servers, Active Directory Federation Services (AD FS) servers, and Active Directory Domain Services (AD DS) domain controllers.</span></span>
  
<span data-ttu-id="c2697-188">Esta configuración tiene los siguientes atributos de aplicaciones LOB en Azure:</span><span class="sxs-lookup"><span data-stu-id="c2697-188">This configuration has the following attributes of LOB applications in Azure:</span></span>
  
- <span data-ttu-id="c2697-189">**Niveles:** Hay niveles para los servidores proxy Web, los servidores de AD FS y los controladores de dominio de AD DS.</span><span class="sxs-lookup"><span data-stu-id="c2697-189">**Tiers:** There are tiers for web proxy servers, AD FS servers, and AD DS domain controllers.</span></span>
    
- <span data-ttu-id="c2697-190">**Distribución de carga:** Un equilibrador de carga de Azure externo distribuye las solicitudes de autenticación de cliente entrantes a los proxy web y un equilibrador de carga interno de Azure distribuye las solicitudes de autenticación a los servidores de AD FS.</span><span class="sxs-lookup"><span data-stu-id="c2697-190">**Load distribution:** An external Azure load balancer distributes the incoming client authentication requests to the web proxies and an internal Azure load balancer distributes authentication requests to the AD FS servers.</span></span>
    
<span data-ttu-id="c2697-191">Siga esta ruta de acceso para una adopción correcta:</span><span class="sxs-lookup"><span data-stu-id="c2697-191">Follow this path for successful adoption:</span></span>
  
1. <span data-ttu-id="c2697-192">Evaluar y experimentar</span><span class="sxs-lookup"><span data-stu-id="c2697-192">Evaluate and experiment</span></span>
    
    <span data-ttu-id="c2697-193">Consulte [Federated Identity for your Office 365 dev/test Environment](federated-identity-for-your-office-365-dev-test-environment.md) para crear un entorno de pruebas y desarrollo simulado para la autenticación federada con Office 365.</span><span class="sxs-lookup"><span data-stu-id="c2697-193">See [Federated identity for your Office 365 dev/test environment](federated-identity-for-your-office-365-dev-test-environment.md) to build a simulated dev/test environment for federated authentication with Office 365.</span></span>
    
2. <span data-ttu-id="c2697-194">Implementar</span><span class="sxs-lookup"><span data-stu-id="c2697-194">Deploy</span></span>
    
    <span data-ttu-id="c2697-195">Consulte [deploy High Availability Federated Authentication for Office 365 en Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) para recorrer la configuración de un extremo a otro de la infraestructura de AD FS de alta disponibilidad en cinco fases.</span><span class="sxs-lookup"><span data-stu-id="c2697-195">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) to step through the end-to-end configuration of the high availability AD FS infrastructure in five phases.</span></span>
    
    
## <a name="see-also"></a><span data-ttu-id="c2697-196">Vea también</span><span class="sxs-lookup"><span data-stu-id="c2697-196">See Also</span></span>

[<span data-ttu-id="c2697-197">Microsoft Hybrid Cloud para arquitectos profesionales</span><span class="sxs-lookup"><span data-stu-id="c2697-197">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="c2697-198">Recursos de arquitectura de TI de Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="c2697-198">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)


