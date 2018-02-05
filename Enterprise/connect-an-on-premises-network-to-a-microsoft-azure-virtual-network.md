---
title: Conectar una red local con una red virtual de Microsoft Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
ms.custom:
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 81190961-5454-4a5c-8b0e-6ae75b9fb035
description: 'Resumen: Aprenda a configurar una red virtual de Azure entre locales para las cargas de trabajo de servidor de Office.'
ms.openlocfilehash: 28afcc083218e7e50fe41ddc8505c9283b15d83d
ms.sourcegitcommit: b3d44b30b6e60df85ea9b404692db64ba54a16c7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2018
---
# <a name="connect-an-on-premises-network-to-a-microsoft-azure-virtual-network"></a><span data-ttu-id="041ab-103">Conectar una red local con una red virtual de Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="041ab-103">Connect an on-premises network to a Microsoft Azure virtual network</span></span>

 <span data-ttu-id="041ab-104">**Resumen:** Aprenda a configurar una red virtual de Azure entre locales para las cargas de trabajo de servidor de Office.</span><span class="sxs-lookup"><span data-stu-id="041ab-104">**Summary:** Learn how to configure a cross-premises Azure virtual network for Office server workloads.</span></span>
  
<span data-ttu-id="041ab-p101">Una red virtual de Azure entre locales está conectada en su red local, ampliando su red para incluir subredes y máquinas virtuales hospedadas en servicios de infraestructura de Azure. Esta conexión permite a los equipos de su red local tener acceso directamente a las máquinas virtuales en Azure y viceversa. Por ejemplo, un servidor de DirSync que se ejecuta en una máquina virtual de Azure necesita consultar los controladores de dominio locales para efectuar cambios en las cuentas y sincronizarlos con su suscripción a Office 365. En este artículo se muestra cómo configurar una red virtual de Azure entre locales que esté lista para hospedar máquinas virtuales de Azure.</span><span class="sxs-lookup"><span data-stu-id="041ab-p101">A cross-premises Azure virtual network is connected to your on-premises network, extending your network to include subnets and virtual machines hosted in Azure infrastructure services. This connection allows computers on your on-premises network to directly access virtual machines in Azure and vice versa. For example, a DirSync server running on an Azure virtual machine needs to query your on-premises domain controllers for changes to accounts and synchronize those changes with your Office 365 subscription. This article shows you how to set up a cross-premises Azure virtual network that is ready to host Azure virtual machines.</span></span>

## <a name="overview"></a><span data-ttu-id="041ab-109">Información general</span><span class="sxs-lookup"><span data-stu-id="041ab-109">Overview</span></span>

<span data-ttu-id="041ab-p102">Las máquinas virtuales en Azure no tienen que estar aisladas de su entorno local. Para conectar máquinas virtuales de Azure en sus recursos de red locales, debe configurar una red virtual de Azure entre locales. En el siguiente diagrama se muestran los componentes requeridos para implementar una red virtual de Azure entre locales con una máquina virtual en Azure.</span><span class="sxs-lookup"><span data-stu-id="041ab-p102">Your virtual machines in Azure don't have to be isolated from your on-premises environment. To connect Azure virtual machines to your on-premises network resources, you must configure a cross-premises Azure virtual network. The following diagram shows the required components to deploy a cross-premises Azure virtual network with a virtual machine in Azure.</span></span>
  
![Red local conectada a Microsoft Azure mediante una conexión VPN de sitio a sitio.](images/CP_ConnectOnPremisesNetworkToAzureVPN.png)
  
<span data-ttu-id="041ab-p103">En el diagrama, existen dos redes conectadas mediante una conexión de red privada virtual (VPN) de sitio a sitio: la red local y la red virtual de Azure. La conexión VPN de sitio a sitio finaliza mediante un dispositivo VPN en la red local y una puerta de enlace VPN de Azure en la red virtual de Azure que tiene máquinas virtuales. El tráfico de red que se origina desde las máquinas virtuales en la red virtual de Azure se reenvía a la puerta de enlace VPN, que posteriormente reenvía el tráfico por la conexión VPN de sitio a sitio al dispositivo VPN en la red local. La infraestructura de enrutamiento de la red local reenvía después el tráfico a su destino.</span><span class="sxs-lookup"><span data-stu-id="041ab-p103">In the diagram, there are two networks connected by a site-to-site virtual private network (VPN) connection: the on-premises network and the Azure virtual network. The site-to-site VPN connection is terminated by a VPN device on the on-premises network and an Azure VPN gateway on the Azure virtual network. The Azure virtual network has virtual machines. Network traffic originating from virtual machines on the Azure virtual network gets forwarded to the VPN gateway, which then forwards the traffic across the site-to-site VPN connection to the VPN device on the on-premises network. The routing infrastructure of the on-premises network then forwards the traffic to its destination.</span></span>
  
<span data-ttu-id="041ab-119">Para configurar la conexión VPN entre la red virtual de Azure y su red local, haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="041ab-119">To set up the VPN connection between your Azure virtual network and your on-premises network, do the following steps:</span></span> 
  
1. <span data-ttu-id="041ab-120">**Local:** Defina y cree una ruta de red local para el espacio de direcciones de la red virtual de Azure que señale a su dispositivo de VPN local.</span><span class="sxs-lookup"><span data-stu-id="041ab-120">**On-premises:** Define and create an on-premises network route for the address space of the Azure virtual network that points to your on-premises VPN device.</span></span>
    
2. <span data-ttu-id="041ab-p104">**Microsoft Azure:** cree una red virtual de Azure con una conexión VPN de sitio a sitio. En este artículo no se describe el uso de [ExpressRoute](https://azure.microsoft.com/services/expressroute/).</span><span class="sxs-lookup"><span data-stu-id="041ab-p104">**Microsoft Azure:** Create an Azure virtual network with a site-to-site VPN connection. This article does not describe the use of [ExpressRoute](https://azure.microsoft.com/services/expressroute/).</span></span>
    
3. <span data-ttu-id="041ab-123">**Local:** Configure el dispositivo de VPN de hardware o software local para finalizar la conexión de VPN, que usa el Protocolo de seguridad de Internet (IPsec).</span><span class="sxs-lookup"><span data-stu-id="041ab-123">**On premises:** Configure your on-premises hardware or software VPN device to terminate the VPN connection, which uses Internet Protocol security (IPsec).</span></span>
    
<span data-ttu-id="041ab-124">Después de establecer la conexión VPN de sitio a sitio, agregue máquinas virtuales de Azure a las subredes de la red virtual.</span><span class="sxs-lookup"><span data-stu-id="041ab-124">After you establish the site-to-site VPN connection, you add Azure virtual machines to the subnets of the virtual network.</span></span>
  
## <a name="plan-your-azure-virtual-network"></a><span data-ttu-id="041ab-125">Planear la red virtual de Azure</span><span class="sxs-lookup"><span data-stu-id="041ab-125">Plan your Azure virtual network</span></span>
<a name="PlanningVirtual"></a>

### <a name="prerequisites"></a><span data-ttu-id="041ab-126">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="041ab-126">Prerequisites</span></span>
<a name="Prerequisites"></a>

- <span data-ttu-id="041ab-p105">Una suscripción a Azure. Para información sobre suscripciones a Azure, vaya a la [página de suscripción a Microsoft Azure](https://azure.microsoft.com/pricing/purchase-options/).</span><span class="sxs-lookup"><span data-stu-id="041ab-p105">An Azure subscription. For information about Azure subscriptions, go to the [Microsoft Azure subscription page](https://azure.microsoft.com/pricing/purchase-options/).</span></span>
    
- <span data-ttu-id="041ab-129">Un espacio de direcciones IPv4 privadas que está disponible y que se puede asignar a la red virtual y sus subredes, con suficiente espacio para albergar el incremento en el número de máquinas virtuales necesarias ahora y en el futuro.</span><span class="sxs-lookup"><span data-stu-id="041ab-129">An available private IPv4 address space to assign to the virtual network and its subnets, with sufficient room for growth to accommodate the number of virtual machines needed now and in the future.</span></span>
    
- <span data-ttu-id="041ab-p106">Un dispositivo VPN disponible en la red local para finalizar la conexión VPN de sitio a sitio que admite los requisitos para IPsec. Para obtener más información, consulte [Acerca de los dispositivos VPN para las conexiones de red virtual de sitio a sitio](https://go.microsoft.com/fwlink/p/?LinkId=393093).</span><span class="sxs-lookup"><span data-stu-id="041ab-p106">An available VPN device in your on-premises network to terminate the site-to-site VPN connection that supports the requirements for IPsec. For more information, see [About VPN devices for site-to-site virtual network connections](https://go.microsoft.com/fwlink/p/?LinkId=393093).</span></span>
    
- <span data-ttu-id="041ab-132">Cambios en la infraestructura de enrutamiento de modo que el tráfico enrutado al espacio de direcciones de la red virtual de Azure se reenvía al dispositivo VPN que hospeda a la conexión VPN de sitio a sitio.</span><span class="sxs-lookup"><span data-stu-id="041ab-132">Changes to your routing infrastructure so that traffic routed to the address space of the Azure virtual network gets forwarded to the VPN device that hosts the site-to-site VPN connection.</span></span>
    
- <span data-ttu-id="041ab-133">Un proxy web que da acceso a Internet a los equipos que están conectados a la red local y la red virtual de Azure.</span><span class="sxs-lookup"><span data-stu-id="041ab-133">A web proxy that gives computers that are connected to the on-premises network and the Azure virtual network access to the Internet.</span></span>
    
### <a name="solution-architecture-design-assumptions"></a><span data-ttu-id="041ab-134">Suposiciones de diseño de la arquitectura de la solución</span><span class="sxs-lookup"><span data-stu-id="041ab-134">Solution architecture design assumptions</span></span>

<span data-ttu-id="041ab-135">En la siguiente lista se representan las elecciones de diseño que se han tomado para la arquitectura de esta solución.</span><span class="sxs-lookup"><span data-stu-id="041ab-135">The following list represents the design choices that have been made for this solution architecture.</span></span> 
  
- <span data-ttu-id="041ab-p107">Esta solución usa una sola red virtual de Azure con una conexión VPN de sitio a sitio. La red virtual de Azure hospeda a una sola subred que puede contener varias máquinas virtuales.</span><span class="sxs-lookup"><span data-stu-id="041ab-p107">This solution uses a single Azure virtual network with a site-to-site VPN connection. The Azure virtual network hosts a single subnet that can contain multiple virtual machines.</span></span> 
    
- <span data-ttu-id="041ab-p108">Puede usar el Servicio de enrutamiento y acceso remoto (RRAS) en Windows Server 2016 o Windows Server 2012 para establecer una conexión VPN de sitio a sitio de IPsec entre la red local y la red virtual de Azure. También puede usar otras opciones, como dispositivos VPN de Cisco o Juniper Networks.</span><span class="sxs-lookup"><span data-stu-id="041ab-p108">You can use the Routing and Remote Access Service (RRAS) in Windows Server 2016 or Windows Server 2012 to establish an IPsec site-to-site VPN connection between the on-premises network and the Azure virtual network. You can also use other options, such as Cisco or Juniper Networks VPN devices.</span></span>
    
- <span data-ttu-id="041ab-p109">La red local aún podría tener servicios de red como Windows Server Active Directory (AD), Sistema de nombres de dominio (DNS) y servidores proxy. Según los requisitos, podría resultar conveniente colocar algunos de estos recursos de red en la red virtual de Azure.</span><span class="sxs-lookup"><span data-stu-id="041ab-p109">The on-premises network might still have network services like Windows Server Active Directory (AD), Domain Name System (DNS), and proxy servers. Depending on your requirements, it might be beneficial to place some of these network resources in the Azure virtual network.</span></span>
    
<span data-ttu-id="041ab-p110">Para una red virtual de Azure existente con una subred o más, determine si queda espacio de direcciones para que una subred adicional hospede las máquinas virtuales que necesita, en función de los requisitos. Si no le queda más espacio de direcciones para una subred adicional, cree una red virtual adicional que tenga su propia conexión VPN de sitio a sitio.</span><span class="sxs-lookup"><span data-stu-id="041ab-p110">For an existing Azure virtual network with one or more subnets, determine whether there is remaining address space for an additional subnet to host your needed virtual machines, based on your requirements. If you don't have remaining address space for an additional subnet, create an additional virtual network that has its own site-to-site VPN connection.</span></span>
  
### <a name="plan-the-routing-infrastructure-changes-for-the-azure-virtual-network"></a><span data-ttu-id="041ab-144">Planear los cambios de infraestructura de enrutamiento de la red virtual de Azure</span><span class="sxs-lookup"><span data-stu-id="041ab-144">Plan the routing infrastructure changes for the Azure virtual network</span></span>

<span data-ttu-id="041ab-145">Debe configurar la infraestructura de enrutamiento local para reenviar tráfico destinado para el espacio de direcciones de la red virtual de Azure al dispositivo VPN local que está hospedando la conexión VPN de sitio a sitio.</span><span class="sxs-lookup"><span data-stu-id="041ab-145">You must configure your on-premises routing infrastructure to forward traffic destined for the address space of the Azure virtual network to the on-premises VPN device that is hosting the site-to-site VPN connection.</span></span>
  
<span data-ttu-id="041ab-146">El método exacto de actualizar su infraestructura de enrutamiento depende de cómo administra la información de enrutamiento, que puede ser:</span><span class="sxs-lookup"><span data-stu-id="041ab-146">The exact method of updating your routing infrastructure depends on how you manage routing information, which can be:</span></span>
  
- <span data-ttu-id="041ab-147">Actualizaciones de tabla de enrutamiento basadas en configuración manual.</span><span class="sxs-lookup"><span data-stu-id="041ab-147">Routing table updates based on manual configuration.</span></span>
    
- <span data-ttu-id="041ab-148">Actualizaciones de tabla de enrutamiento basadas en protocolos de enrutamiento, como Protocolo de información de enrutamiento (RIP) o Abrir ruta de acceso más corta primero (OSPF).</span><span class="sxs-lookup"><span data-stu-id="041ab-148">Routing table updates based on routing protocols, such as Routing Information Protocol (RIP) or Open Shortest Path First (OSPF).</span></span>
    
<span data-ttu-id="041ab-149">Consulte con su especialista en enrutamiento para asegurarse de que el tráfico destinado a la red virtual de Azure se reenvía al dispositivo de VPN local.</span><span class="sxs-lookup"><span data-stu-id="041ab-149">Consult with your routing specialist to make sure that traffic destined for the Azure virtual network is forwarded to the on-premises VPN device.</span></span>
  
### <a name="plan-for-firewall-rules-for-traffic-to-and-from-the-on-premises-vpn-device"></a><span data-ttu-id="041ab-150">Planear para reglas de firewall para tráfico desde el dispositivo VPN local y hacia el dispositivo</span><span class="sxs-lookup"><span data-stu-id="041ab-150">Plan for firewall rules for traffic to and from the on-premises VPN device</span></span>

<span data-ttu-id="041ab-151">Si el dispositivo VPN está en una red perimetral que tiene un firewall entre la red perimetral e Internet, es posible que deba configurar el firewall para las siguientes reglas a fin de permitir la conexión de VPN de sitio a sitio.</span><span class="sxs-lookup"><span data-stu-id="041ab-151">If your VPN device is on a perimeter network that has a firewall between the perimeter network and the Internet, you might have to configure the firewall for the following rules to allow the site-to-site VPN connection.</span></span>
  
- <span data-ttu-id="041ab-152">Tráfico al dispositivo VPN (entrante desde Internet):</span><span class="sxs-lookup"><span data-stu-id="041ab-152">Traffic to the VPN device (incoming from the Internet):</span></span>
    
  - <span data-ttu-id="041ab-153">Dirección IP de destino del dispositivo VPN y protocolo IP 50</span><span class="sxs-lookup"><span data-stu-id="041ab-153">Destination IP address of the VPN device and IP protocol 50</span></span>
    
  - <span data-ttu-id="041ab-154">Dirección IP de destino del dispositivo VPN y puerto de destino UDP 500</span><span class="sxs-lookup"><span data-stu-id="041ab-154">Destination IP address of the VPN device and UDP destination port 500</span></span>
    
  - <span data-ttu-id="041ab-155">Dirección IP de destino del dispositivo VPN y puerto de destino UDP 4500</span><span class="sxs-lookup"><span data-stu-id="041ab-155">Destination IP address of the VPN device and UDP destination port 4500</span></span>
    
- <span data-ttu-id="041ab-156">Tráfico desde el dispositivo VPN (saliente a Internet):</span><span class="sxs-lookup"><span data-stu-id="041ab-156">Traffic from the VPN device (outgoing to the Internet):</span></span>
    
  - <span data-ttu-id="041ab-157">Dirección IP de origen del dispositivo VPN y protocolo IP 50</span><span class="sxs-lookup"><span data-stu-id="041ab-157">Source IP address of the VPN device and IP protocol 50</span></span>
    
  - <span data-ttu-id="041ab-158">Dirección IP de origen del dispositivo VPN y puerto de origen UDP 500</span><span class="sxs-lookup"><span data-stu-id="041ab-158">Source IP address of the VPN device and UDP source port 500</span></span>
    
  - <span data-ttu-id="041ab-159">Dirección IP de origen del dispositivo VPN y puerto de origen UDP 4500</span><span class="sxs-lookup"><span data-stu-id="041ab-159">Source IP address of the VPN device and UDP source port 4500</span></span>
    
### <a name="plan-for-the-private-ip-address-space-of-the-azure-virtual-network"></a><span data-ttu-id="041ab-160">Planear el espacio de direcciones IP privadas de la red virtual de Azure</span><span class="sxs-lookup"><span data-stu-id="041ab-160">Plan for the private IP address space of the Azure virtual network</span></span>

<span data-ttu-id="041ab-161">El espacio de direcciones IP privadas de la red virtual de Azure debe poder albergar las direcciones utilizadas por Azure para hospedar a la red virtual con al menos una subred que tenga suficientes direcciones para sus máquinas virtuales de Azure.</span><span class="sxs-lookup"><span data-stu-id="041ab-161">The private IP address space of the Azure virtual network must be able to accommodate addresses used by Azure to host the virtual network and with at least one subnet that has enough addresses for your Azure virtual machines.</span></span>
  
<span data-ttu-id="041ab-162">Para determinar el número de direcciones necesarias para la subred, cuente el número de máquinas virtuales que necesita ahora, estime el crecimiento futuro y luego use la siguiente tabla para determinar el tamaño de la subred.</span><span class="sxs-lookup"><span data-stu-id="041ab-162">To determine the number of addresses needed for the subnet, count the number of virtual machines that you need now, estimate for future growth, and then use the following table to determine the size of the subnet.</span></span>
  
|<span data-ttu-id="041ab-163">**Número de máquinas virtuales necesarias**</span><span class="sxs-lookup"><span data-stu-id="041ab-163">**Number of virtual machines needed**</span></span>|<span data-ttu-id="041ab-164">**Número de bits de host necesarios**</span><span class="sxs-lookup"><span data-stu-id="041ab-164">**Number of host bits needed**</span></span>|<span data-ttu-id="041ab-165">**Tamaño de la subred**</span><span class="sxs-lookup"><span data-stu-id="041ab-165">**Size of the subnet**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="041ab-166">1-3</span><span class="sxs-lookup"><span data-stu-id="041ab-166">1-3</span></span>  <br/> |<span data-ttu-id="041ab-167">3</span><span class="sxs-lookup"><span data-stu-id="041ab-167">3.</span></span>  <br/> |<span data-ttu-id="041ab-168">/29</span><span class="sxs-lookup"><span data-stu-id="041ab-168">/29</span></span>  <br/> |
|<span data-ttu-id="041ab-169">4-11</span><span class="sxs-lookup"><span data-stu-id="041ab-169">4-11</span></span>  <br/> |<span data-ttu-id="041ab-170">4</span><span class="sxs-lookup"><span data-stu-id="041ab-170">4.</span></span>  <br/> |<span data-ttu-id="041ab-171">/28</span><span class="sxs-lookup"><span data-stu-id="041ab-171">/28</span></span>  <br/> |
|<span data-ttu-id="041ab-172">12-27</span><span class="sxs-lookup"><span data-stu-id="041ab-172">12-27</span></span>  <br/> |<span data-ttu-id="041ab-173">5</span><span class="sxs-lookup"><span data-stu-id="041ab-173">5.</span></span>  <br/> |<span data-ttu-id="041ab-174">/27</span><span class="sxs-lookup"><span data-stu-id="041ab-174">/27</span></span>  <br/> |
|<span data-ttu-id="041ab-175">28-59</span><span class="sxs-lookup"><span data-stu-id="041ab-175">28-59</span></span>  <br/> |<span data-ttu-id="041ab-176">6</span><span class="sxs-lookup"><span data-stu-id="041ab-176">6.</span></span>  <br/> |<span data-ttu-id="041ab-177">/26</span><span class="sxs-lookup"><span data-stu-id="041ab-177">/26</span></span>  <br/> |
|<span data-ttu-id="041ab-178">60-123</span><span class="sxs-lookup"><span data-stu-id="041ab-178">60-123</span></span>  <br/> |<span data-ttu-id="041ab-179">7</span><span class="sxs-lookup"><span data-stu-id="041ab-179">7.</span></span>  <br/> |<span data-ttu-id="041ab-180">/25</span><span class="sxs-lookup"><span data-stu-id="041ab-180">/25</span></span>  <br/> |
   
### <a name="planning-worksheet-for-configuring-your-azure-virtual-network"></a><span data-ttu-id="041ab-181">Planear la hoja de cálculo para configurar la red virtual de Azure</span><span class="sxs-lookup"><span data-stu-id="041ab-181">Planning worksheet for configuring your Azure virtual network</span></span>
<span data-ttu-id="041ab-182"><a name="worksheet"> </a></span><span class="sxs-lookup"><span data-stu-id="041ab-182"></span></span>

<span data-ttu-id="041ab-183">Antes de crear una red virtual de Azure para hospedar las máquinas virtuales, debe determinar la configuración necesaria en las tablas siguientes.</span><span class="sxs-lookup"><span data-stu-id="041ab-183">Before you create an Azure virtual network to host virtual machines, you must determine the settings needed in the following tables.</span></span>
  
<span data-ttu-id="041ab-184">Para la configuración de la red virtual, rellene la Tabla V.</span><span class="sxs-lookup"><span data-stu-id="041ab-184">For the settings of the virtual network, fill in Table V.</span></span>
  
 <span data-ttu-id="041ab-185">**Tabla V: Configuración de la red virtual entre locales**</span><span class="sxs-lookup"><span data-stu-id="041ab-185">**Table V: Cross-premises virtual network configuration**</span></span>
  
|<span data-ttu-id="041ab-186">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="041ab-186">**Item**</span></span>|<span data-ttu-id="041ab-187">**Elemento Configuration**</span><span class="sxs-lookup"><span data-stu-id="041ab-187">**Configuration element**</span></span>|<span data-ttu-id="041ab-188">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="041ab-188">**Description**</span></span>|<span data-ttu-id="041ab-189">**Valor**</span><span class="sxs-lookup"><span data-stu-id="041ab-189">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="041ab-190">1.</span><span class="sxs-lookup"><span data-stu-id="041ab-190">1.</span></span>  <br/> |<span data-ttu-id="041ab-191">Nombre de la red virtual</span><span class="sxs-lookup"><span data-stu-id="041ab-191">Virtual network name</span></span>  <br/> |<span data-ttu-id="041ab-192">Nombre que se va a asignar a la red virtual de Azure (por ejemplo, DirSyncNet).</span><span class="sxs-lookup"><span data-stu-id="041ab-192">A name to assign to the Azure virtual network (example DirSyncNet).</span></span>  <br/> |<span data-ttu-id="041ab-193">_ _ _ _ _ _ _ _ _</span><span class="sxs-lookup"><span data-stu-id="041ab-193"></span></span> <br/> |
|<span data-ttu-id="041ab-194">2.</span><span class="sxs-lookup"><span data-stu-id="041ab-194">2.</span></span>  <br/> |<span data-ttu-id="041ab-195">Ubicación de la red virtual</span><span class="sxs-lookup"><span data-stu-id="041ab-195">Virtual network location</span></span>  <br/> |<span data-ttu-id="041ab-196">Centro de datos de Azure que contendrá la red virtual (por ejemplo, Oeste de EE. UU.).</span><span class="sxs-lookup"><span data-stu-id="041ab-196">The Azure datacenter that will contain the virtual network (such as West US).</span></span>  <br/> |<span data-ttu-id="041ab-197">_ _ _ _ _ _ _ _ _</span><span class="sxs-lookup"><span data-stu-id="041ab-197"></span></span>  <br/> |
|<span data-ttu-id="041ab-198">3.</span><span class="sxs-lookup"><span data-stu-id="041ab-198">3.</span></span>  <br/> |<span data-ttu-id="041ab-199">Dirección IP del dispositivo VPN</span><span class="sxs-lookup"><span data-stu-id="041ab-199">VPN device IP address</span></span>  <br/> |<span data-ttu-id="041ab-p111">Dirección IPv4 pública de la interfaz del dispositivo VPN en Internet. Colabore con su departamento de TI para determinar esta dirección.</span><span class="sxs-lookup"><span data-stu-id="041ab-p111">The public IPv4 address of your VPN device's interface on the Internet. Work with your IT department to determine this address.</span></span>  <br/> |<span data-ttu-id="041ab-202">_ _ _ _ _ _ _ _ _</span><span class="sxs-lookup"><span data-stu-id="041ab-202"></span></span>  <br/> |
|<span data-ttu-id="041ab-203">4.</span><span class="sxs-lookup"><span data-stu-id="041ab-203">4.</span></span>  <br/> |<span data-ttu-id="041ab-204">Espacio de direcciones de la red virtual</span><span class="sxs-lookup"><span data-stu-id="041ab-204">Virtual network address space</span></span>  <br/> |<span data-ttu-id="041ab-p112">Espacio de direcciones (definido en un único prefijo de dirección privada) para la red virtual. Colabore con su departamento de TI para determinar este espacio de direcciones. El espacio de direcciones debe estar en formato de Enrutamiento de interdominios sin clases (CIDR), también conocido como formato de prefijo de red. Por ejemplo, 10.24.64.0/20.</span><span class="sxs-lookup"><span data-stu-id="041ab-p112">The address space (defined in a single private address prefix) for the virtual network. Work with your IT department to determine this address space. The address space should be in Classless Interdomain Routing (CIDR) format, also known as network prefix format. An example is 10.24.64.0/20.</span></span>  <br/> |<span data-ttu-id="041ab-209">_ _ _ _ _ _ _ _ _</span><span class="sxs-lookup"><span data-stu-id="041ab-209"></span></span>  <br/> |
|<span data-ttu-id="041ab-210">5.</span><span class="sxs-lookup"><span data-stu-id="041ab-210">5.</span></span>  <br/> |<span data-ttu-id="041ab-211">Clave compartida IPsec</span><span class="sxs-lookup"><span data-stu-id="041ab-211">IPsec shared key</span></span>  <br/> |<span data-ttu-id="041ab-p113">Cadena alfanumérica aleatoria de 32 caracteres que se usará para autenticar ambos lados de la conexión VPN de sitio a sitio. Colabore con su departamento de TI o de seguridad para determinar el valor de esta clave y después almacénelo en una ubicación segura. También puede consultar [Crear una cadena aleatoria para una clave precompartida IPsec](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).</span><span class="sxs-lookup"><span data-stu-id="041ab-p113">A 32-character random, alphanumeric string that will be used to authenticate both sides of the site-to-site VPN connection. Work with your IT or security department to determine this key value and then store it in a secure location. Alternately, see [Create a random string for an IPsec preshared key](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  </span></span><br/> |<span data-ttu-id="041ab-215">_ _ _ _ _ _ _ _ _</span><span class="sxs-lookup"><span data-stu-id="041ab-215"></span></span>  <br/> |
   
<span data-ttu-id="041ab-216">Rellene la Tabla S para las subredes de esta solución.</span><span class="sxs-lookup"><span data-stu-id="041ab-216">Fill in Table S for the subnets of this solution.</span></span>
  
- <span data-ttu-id="041ab-p114">Para la primera subred, determine un espacio de direcciones de 28 bits (con una longitud de prefijo /28) para la subred de puerta de enlace de Azure. Consulte [Calcular el espacio de direcciones de la subred de puerta de enlace para las redes virtuales de Azure](https://blogs.technet.microsoft.com/solutions_advisory_board/2016/12/01/calculating-the-gateway-subnet-address-space-for-azure-virtual-networks/) para obtener información sobre cómo determinar este espacio de direcciones.</span><span class="sxs-lookup"><span data-stu-id="041ab-p114">For the first subnet, determine a 28-bit address space (with a /28 prefix length) for the Azure gateway subnet. See [Calculating the gateway subnet address space for Azure virtual networks](https://blogs.technet.microsoft.com/solutions_advisory_board/2016/12/01/calculating-the-gateway-subnet-address-space-for-azure-virtual-networks/) for information about how to determine this address space.</span></span>
    
- <span data-ttu-id="041ab-219">Para la segunda subred, especifique un nombre descriptivo, un único espacio de direcciones IP basado en el espacio de direcciones de la red virtual y una finalidad descriptiva.</span><span class="sxs-lookup"><span data-stu-id="041ab-219">For the second subnet, specify a friendly name, a single IP address space based on the virtual network address space, and a descriptive purpose.</span></span>
    
<span data-ttu-id="041ab-p115">Colabore con su departamento de TI para determinar estos espacios de direcciones a partir del espacio de direcciones de la red virtual. Ambos espacios de direcciones deben estar en formato CIDR.</span><span class="sxs-lookup"><span data-stu-id="041ab-p115">Work with your IT department to determine these address spaces from the virtual network address space. Both address spaces should be in CIDR format.</span></span>
  
 <span data-ttu-id="041ab-222">**Tabla S: Subredes de la red virtual**</span><span class="sxs-lookup"><span data-stu-id="041ab-222">**Table S: Subnets in the virtual network**</span></span>
  
|<span data-ttu-id="041ab-223">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="041ab-223">**Item**</span></span>|<span data-ttu-id="041ab-224">**Nombre de la subred**</span><span class="sxs-lookup"><span data-stu-id="041ab-224">**Subnet name**</span></span>|<span data-ttu-id="041ab-225">**Espacio de direcciones de la subred**</span><span class="sxs-lookup"><span data-stu-id="041ab-225">**Subnet address space**</span></span>|<span data-ttu-id="041ab-226">**Finalidad**</span><span class="sxs-lookup"><span data-stu-id="041ab-226">**Purpose**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="041ab-227">1.</span><span class="sxs-lookup"><span data-stu-id="041ab-227">1.</span></span>  <br/> |<span data-ttu-id="041ab-228">GatewaySubnet</span><span class="sxs-lookup"><span data-stu-id="041ab-228">GatewaySubnet</span></span>  <br/> |<span data-ttu-id="041ab-229">_ _ _ _ _ _ _ _ _</span><span class="sxs-lookup"><span data-stu-id="041ab-229"></span></span>  <br/> |<span data-ttu-id="041ab-230">Subred usada por la puerta de enlace de Azure.</span><span class="sxs-lookup"><span data-stu-id="041ab-230">The subnet used by the Azure gateway.</span></span>  <br/> |
|<span data-ttu-id="041ab-231">2.</span><span class="sxs-lookup"><span data-stu-id="041ab-231">2.</span></span>  <br/> |<span data-ttu-id="041ab-232">_ _ _ _ _ _ _ _ _</span><span class="sxs-lookup"><span data-stu-id="041ab-232"></span></span>  <br/> |<span data-ttu-id="041ab-233">_ _ _ _ _ _ _ _ _</span><span class="sxs-lookup"><span data-stu-id="041ab-233"></span></span>  <br/> |<span data-ttu-id="041ab-234">_ _ _ _ _ _ _ _ _</span><span class="sxs-lookup"><span data-stu-id="041ab-234"></span></span>  <br/> |
   
<span data-ttu-id="041ab-p116">Para los servidores DNS locales que desea que sean usados por las máquinas virtuales de la red virtual, rellene la Tabla D. Asígnele a cada servidor DNS un nombre descriptivo y una única dirección IP. No hace falta que este nombre descriptivo coincida con el nombre de host o con el nombre de equipo del servidor DNS. Observe que aparecen dos entradas en blanco, pero puede agregar más. Colabore con su departamento de TI para determinar esta lista.</span><span class="sxs-lookup"><span data-stu-id="041ab-p116">For the on-premises DNS servers that you want the virtual machines in the virtual network to use, fill in Table D. Give each DNS server a friendly name and a single IP address. This friendly name does not need to match the host name or computer name of the DNS server. Note that two blank entries are listed, but you can add more. Work with your IT department to determine this list.</span></span>
  
 <span data-ttu-id="041ab-239">**Tabla D: Servidores DNS locales**</span><span class="sxs-lookup"><span data-stu-id="041ab-239">**Table D: On-premises DNS servers**</span></span>
  
|<span data-ttu-id="041ab-240">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="041ab-240">**Item**</span></span>|<span data-ttu-id="041ab-241">**Nombre descriptivo del servidor DNS**</span><span class="sxs-lookup"><span data-stu-id="041ab-241">**DNS server friendly name**</span></span>|<span data-ttu-id="041ab-242">**Dirección IP del servidor DNS**</span><span class="sxs-lookup"><span data-stu-id="041ab-242">**DNS server IP address**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="041ab-243">1.</span><span class="sxs-lookup"><span data-stu-id="041ab-243">1.</span></span>  <br/> |<span data-ttu-id="041ab-244">_ _ _ _ _ _ _ _ _</span><span class="sxs-lookup"><span data-stu-id="041ab-244"></span></span>  <br/> |<span data-ttu-id="041ab-245">_ _ _ _ _ _ _ _ _</span><span class="sxs-lookup"><span data-stu-id="041ab-245"></span></span>  <br/> |
|<span data-ttu-id="041ab-246">2.</span><span class="sxs-lookup"><span data-stu-id="041ab-246">2.</span></span>  <br/> |<span data-ttu-id="041ab-247">_ _ _ _ _ _ _ _ _</span><span class="sxs-lookup"><span data-stu-id="041ab-247"></span></span>  <br/> |<span data-ttu-id="041ab-248">_ _ _ _ _ _ _ _ _</span><span class="sxs-lookup"><span data-stu-id="041ab-248"></span></span>  <br/> |
   
<span data-ttu-id="041ab-p117">Para enrutar paquetes desde la red virtual de Azure a la red de su organización a través de la conexión VPN de sitio a sitio, debe configurar la red virtual con una red local. Esta red local contiene una lista de los espacios de direcciones (en formato CIDR) para todas las ubicaciones de la red local de su organización a las que deben llegar las máquinas virtuales de la red virtual. Pueden ser todas las ubicaciones de la red local o bien un subconjunto. La lista de espacios de direcciones que definen la red local debe ser única y no debe solaparse con los espacios de direcciones que se usan para esta red virtual o con sus otras redes virtuales entre locales.</span><span class="sxs-lookup"><span data-stu-id="041ab-p117">To route packets from the Azure virtual network to your organization network across the site-to-site VPN connection, you must configure the virtual network with a local network. This local network contains a list of the address spaces (in CIDR format) for all of the locations on your organization's on-premises network that the virtual machines in the virtual network must reach. This can be all of the locations on the on-premises network or a subset. The list of address spaces that define your local network must be unique and must not overlap with the address spaces used for this virtual network or your other cross-premises virtual networks.</span></span>
  
<span data-ttu-id="041ab-p118">Para el conjunto de espacios de direcciones de la red local, rellene la Tabla L. Fíjese en que aparecen tres entradas en blanco, pero lo normal es que necesite más. Colabore con su departamento de TI para determinar esta lista.</span><span class="sxs-lookup"><span data-stu-id="041ab-p118">For the set of local network address spaces, fill in Table L. Note that three blank entries are listed but you will typically need more. Work with your IT department to determine this list.</span></span>
  
 <span data-ttu-id="041ab-255">**Tabla L: Prefijos de direcciones para la red local**</span><span class="sxs-lookup"><span data-stu-id="041ab-255">**Table L: Address prefixes for the local network**</span></span>
  
|<span data-ttu-id="041ab-256">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="041ab-256">**Item**</span></span>|<span data-ttu-id="041ab-257">**Espacio de direcciones de la red local**</span><span class="sxs-lookup"><span data-stu-id="041ab-257">**Local network address space**</span></span>|
|:-----|:-----|
|<span data-ttu-id="041ab-258">1.</span><span class="sxs-lookup"><span data-stu-id="041ab-258">1.</span></span>  <br/> |<span data-ttu-id="041ab-259">_ _ _ _ _ _ _ _ _</span><span class="sxs-lookup"><span data-stu-id="041ab-259"></span></span>  <br/> |
|<span data-ttu-id="041ab-260">2.</span><span class="sxs-lookup"><span data-stu-id="041ab-260">2.</span></span>  <br/> |<span data-ttu-id="041ab-261">_ _ _ _ _ _ _ _ _</span><span class="sxs-lookup"><span data-stu-id="041ab-261"></span></span>  <br/> |
|<span data-ttu-id="041ab-262">3.</span><span class="sxs-lookup"><span data-stu-id="041ab-262">3.</span></span>  <br/> |<span data-ttu-id="041ab-263">_ _ _ _ _ _ _ _ _</span><span class="sxs-lookup"><span data-stu-id="041ab-263"></span></span>  <br/> |
   
## <a name="deployment-roadmap"></a><span data-ttu-id="041ab-264">Guía de implementación</span><span class="sxs-lookup"><span data-stu-id="041ab-264">Deployment roadmap</span></span>
<span data-ttu-id="041ab-265"><a name="DeploymentRoadmap"> </a></span><span class="sxs-lookup"><span data-stu-id="041ab-265"></span></span>

<span data-ttu-id="041ab-266">La creación de la red virtual entre locales y la adición de máquinas virtuales en Azure consta de tres fases:</span><span class="sxs-lookup"><span data-stu-id="041ab-266">Creating the cross-premises virtual network and adding virtual machines in Azure consists of three phases:</span></span>
  
- <span data-ttu-id="041ab-267">Fase 1: Prepare la red local.</span><span class="sxs-lookup"><span data-stu-id="041ab-267">Phase 1: Prepare your on-premises network.</span></span>
    
- <span data-ttu-id="041ab-268">Fase 2: Cree la red virtual entre locales en Azure.</span><span class="sxs-lookup"><span data-stu-id="041ab-268">Phase 2: Create the cross-premises virtual network in Azure.</span></span>
    
- <span data-ttu-id="041ab-269">Fase 3 (opcional): Agregue máquinas virtuales.</span><span class="sxs-lookup"><span data-stu-id="041ab-269">Phase 3 (Optional): Add virtual machines.</span></span>
    
### <a name="phase-1-prepare-your-on-premises-network"></a><span data-ttu-id="041ab-270">Fase 1: Prepare la red local.</span><span class="sxs-lookup"><span data-stu-id="041ab-270">Phase 1: Prepare your on-premises network</span></span>
<a name="Phase1"></a>

<span data-ttu-id="041ab-p119">Debe configurar su red local con una ruta que señale al tráfico destinado al espacio de direcciones de la red virtual, y que en última instancia proporcione ese tráfico al enrutador en el perímetro de la red local. Consulte con su administrador de red para determinar cómo agregar la ruta a la infraestructura de enrutamiento de su red local.</span><span class="sxs-lookup"><span data-stu-id="041ab-p119">You must configure your on-premises network with a route that points to and ultimately delivers traffic destined for the address space of the virtual network to the router on the edge of the on-premises network. Consult with your network administrator to determine how to add the route to the routing infrastructure of your on-premises network.</span></span>
  
<span data-ttu-id="041ab-273">Esta es la configuración resultante.</span><span class="sxs-lookup"><span data-stu-id="041ab-273">Here is your resulting configuration.</span></span>
  
![La red local debe tener una ruta para el espacio de direcciones de la red virtual que apunte hacia el dispositivo VPN.](images/90bab36b-cb60-4ea5-81d5-4737b696d41c.png)
  
### <a name="phase-2-create-the-cross-premises-virtual-network-in-azure"></a><span data-ttu-id="041ab-275">Fase 2: Cree la red virtual entre locales en Azure.</span><span class="sxs-lookup"><span data-stu-id="041ab-275">Phase 2: Create the cross-premises virtual network in Azure</span></span>
<a name="Phase2"></a>

<span data-ttu-id="041ab-p120">En primer lugar, abra un símbolo del sistema de Azure PowerShell. Si no ha instalado Azure PowerShell, vea [Introducción a los cmdlets de Azure PowerShell](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/).</span><span class="sxs-lookup"><span data-stu-id="041ab-p120">First, open an Azure PowerShell prompt. If you have not installed Azure PowerShell, see [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/).</span></span>
  
> [!NOTE]
> <span data-ttu-id="041ab-p121">Estos comandos son válidos para Azure PowerShell 1.0 y versiones posteriores. Para obtener un archivo de texto que contenga todos los comandos de PowerShell de este artículo, haga clic [aquí](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-commands-for-5c5a7c19).</span><span class="sxs-lookup"><span data-stu-id="041ab-p121">These commands are for Azure PowerShell 1.0 and above. For a text file that contains all the PowerShell commands in this article, click [here](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-commands-for-5c5a7c19).</span></span> 
  
<span data-ttu-id="041ab-280">A continuación, inicie sesión en su cuenta de Azure con este comando.</span><span class="sxs-lookup"><span data-stu-id="041ab-280">Next, login to your Azure account with this command.</span></span>
  
```
Login-AzureRMAccount
```

<span data-ttu-id="041ab-281">Obtenga su nombre de suscripción mediante el comando siguiente.</span><span class="sxs-lookup"><span data-stu-id="041ab-281">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort SubscriptionName | Select SubscriptionName
```

<span data-ttu-id="041ab-p122">Establezca su suscripción de Azure con estos comandos. Reemplace todo el contenido entrecomillado, incluidos los caracteres < y >, por el nombre correcto de la suscripción.</span><span class="sxs-lookup"><span data-stu-id="041ab-p122">Set your Azure subscription with these commands. Replace everything within the quotes, including the < and > characters, with the correct subscription name.</span></span>
  
```
$subscrName="<subscription name>"
Select-AzureRMSubscription -SubscriptionName $subscrName -Current
```

<span data-ttu-id="041ab-p123">Después, cree un nuevo grupo de recursos para su red virtual. Para determinar un nombre único de grupo de recursos, use este comando a fin de enumerar los grupos de recursos existentes.</span><span class="sxs-lookup"><span data-stu-id="041ab-p123">Next, create a new resource group for your virtual network. To determine a unique resource group name, use this command to list your existing resource groups.</span></span>
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="041ab-286">Cree el nuevo grupo de recursos con estos comandos.</span><span class="sxs-lookup"><span data-stu-id="041ab-286">Create your new resource group with these commands.</span></span>
  
```
$rgName="<resource group name>"
$locName="<Table V - Item 2 - Value column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName

```

<span data-ttu-id="041ab-p124">Las máquinas virtuales basadas en el Administrador de recursos requieren una cuenta de almacenamiento basada en el Administrador de recursos. Debe elegir un nombre único global para la cuenta de almacenamiento que únicamente contenga letras minúsculas y números. Puede usar este comando para enumerar las cuentas de almacenamiento existentes.</span><span class="sxs-lookup"><span data-stu-id="041ab-p124">Resource Manager-based virtual machines require a Resource Manager-based storage account. You must pick a globally unique name for your storage account that contains only lowercase letters and numbers. You can use this command to list the existing storage accounts.</span></span>
  
```
Get-AzureRMStorageAccount | Sort Name | Select Name
```

<span data-ttu-id="041ab-290">Use este comando para comprobar si los nombres de las cuenta de almacenamiento de información que se propongan son únicos.</span><span class="sxs-lookup"><span data-stu-id="041ab-290">Use this command to test whether a proposed storage account name is unique.</span></span>
  
```
Get-AzureRmStorageAccountNameAvailability "<proposed name>"
```

<span data-ttu-id="041ab-291">Para crear una nueva cuenta de almacenamiento, ejecute estos comandos.</span><span class="sxs-lookup"><span data-stu-id="041ab-291">To create a new storage account, run these commands.</span></span>
  
```
$rgName="<your new resource group name>"
$locName="<the location of your new resource group>"
$saName="<unique storage account name>"
New-AzureRMStorageAccount -Name $saName -ResourceGroupName $rgName -Type Standard_LRS -Location $locName
```

<span data-ttu-id="041ab-292">A continuación, cree la red virtual de Azure.</span><span class="sxs-lookup"><span data-stu-id="041ab-292">Next, you create the Azure virtual network.</span></span>
  
```
# Fill in the variables from previous values and from Tables V, S, and D
$rgName="<name of your new resource group>"
$locName="<Azure location of your new resource group>"
$vnetName="<Table V - Item 1 - Value column>"
$vnetAddrPrefix="<Table V - Item 4 - Value column>"
$gwSubnetPrefix="<Table S - Item 1 - Subnet address space column>"
$SubnetName="<Table S - Item 2 - Subnet name column>"
$SubnetPrefix="<Table S - Item 2 - Subnet address space column>"
$dnsServers=@( "<Table D - Item 1 - DNS server IP address column>", "<Table D - Item 2 - DNS server IP address column>" )
$locShortName=(Get-AzureRmResourceGroup -Name $rgName).Location

# Create the Azure virtual network and a network security group that allows incoming remote desktop connections to the subnet that is hosting virtual machines
$gatewaySubnet=New-AzureRmVirtualNetworkSubnetConfig -Name "GatewaySubnet" -AddressPrefix $gwSubnetPrefix
$vmSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name $SubnetName -AddressPrefix $SubnetPrefix
New-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName -Location $locName -AddressPrefix $vnetAddrPrefix -Subnet $gatewaySubnet,$vmSubnet -DNSServer $dnsServers
$rule1=New-AzureRMNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzureRMNetworkSecurityGroup -Name $SubnetName -ResourceGroupName $rgName -Location $locShortName -SecurityRules $rule1
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name $vnetName
$nsg=Get-AzureRMNetworkSecurityGroup -Name $SubnetName -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $SubnetName -AddressPrefix $SubnetPrefix -NetworkSecurityGroup $nsg
```

<span data-ttu-id="041ab-293">Esta es la configuración resultante.</span><span class="sxs-lookup"><span data-stu-id="041ab-293">Here is your resulting configuration.</span></span>
  
![La red virtual aún no está conectada a la red local.](images/54a37782-a6cc-4d48-b38d-73e128b44a82.png)
  
<span data-ttu-id="041ab-295">Después, use estos comandos para crear las puertas de enlace para la conexión VPN de sitio a sitio.</span><span class="sxs-lookup"><span data-stu-id="041ab-295">Next, use these commands to create the gateways for the site-to-site VPN connection.</span></span>
  
```
# Fill in the variables from previous values and from Tables V and L
$vnetName="<Table V - Item 1 - Value column>"
$localGatewayIP="<Table V - Item 3 - Value column>"
$localNetworkPrefix=@( <comma-separated, double-quote enclosed list of the local network address prefixes from Table L, example: "10.1.0.0/24", "10.2.0.0/24"> )
$vnetConnectionKey="<Table V - Item 5 - Value column>"
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
# Attach a virtual network gateway to a public IP address and the gateway subnet
$publicGatewayVipName="PublicIPAddress"
$vnetGatewayIpConfigName="PublicIPConfig"
New-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$publicGatewayVip=Get-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName
$vnetGatewayIpConfig=New-AzureRMVirtualNetworkGatewayIpConfig -Name $vnetGatewayIpConfigName -PublicIpAddressId $publicGatewayVip.Id -SubnetId $vnet.Subnets[0].Id
# Create the Azure gateway
$vnetGatewayName="AzureGateway"
$vnetGateway=New-AzureRMVirtualNetworkGateway -Name $vnetGatewayName -ResourceGroupName $rgName -Location $locName -GatewayType Vpn -VpnType RouteBased -IpConfigurations $vnetGatewayIpConfig
# Create the gateway for the local network
$localGatewayName="LocalNetGateway"
$localGateway=New-AzureRMLocalNetworkGateway -Name $localGatewayName -ResourceGroupName $rgName -Location $locName -GatewayIpAddress $localGatewayIP -AddressPrefix $localNetworkPrefix
# Create the Azure virtual network VPN connection
$vnetConnectionName="S2SConnection"
$vnetConnection=New-AzureRMVirtualNetworkGatewayConnection -Name $vnetConnectionName -ResourceGroupName $rgName -Location $locName -ConnectionType IPsec -SharedKey $vnetConnectionKey -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localGateway
```

<span data-ttu-id="041ab-296">Esta es la configuración resultante.</span><span class="sxs-lookup"><span data-stu-id="041ab-296">Here is your resulting configuration.</span></span>
  
![La red virtual ahora tiene una puerta de enlace.](images/82dd66b2-a4b7-48f6-a89b-cfdd94630980.png)
  
<span data-ttu-id="041ab-p125">Luego configure el dispositivo VPN local para conectarse a la puerta de enlace VPN de Azure. Para obtener más información, consulte [Acerca de los dispositivos VPN para las conexiones de puerta de enlace de VPN de sitio a sitio](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span><span class="sxs-lookup"><span data-stu-id="041ab-p125">Next, configure your on-premises VPN device to connect to the Azure VPN gateway. For more information, see [About VPN Devices for site-to-site Azure Virtual Network connections](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="041ab-300">Para configurar el dispositivo VPN, necesita lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="041ab-300">To configure your VPN device, you will need the following:</span></span>
  
- <span data-ttu-id="041ab-p126">La dirección IPv4 pública de la puerta de enlace de la VPN de Azure de su red virtual. Use el comando **Get-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName** para mostrar esta dirección.</span><span class="sxs-lookup"><span data-stu-id="041ab-p126">The public IPv4 address of the Azure VPN gateway for your virtual network. Use the **Get-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName** command to display this address.</span></span>
    
- <span data-ttu-id="041ab-303">La clave precompartida IPsec para la conexión VPN de sitio a sitio (Tabla V, elemento 5, columna Valor).</span><span class="sxs-lookup"><span data-stu-id="041ab-303">The IPsec pre-shared key for the site-to-site VPN connection (Table V- Item 5 - Value column).</span></span>
    
<span data-ttu-id="041ab-304">Esta es la configuración resultante.</span><span class="sxs-lookup"><span data-stu-id="041ab-304">Here is your resulting configuration.</span></span>
  
![La red virtual está ahora conectada a la red local.](images/6379c423-4f22-4453-941b-7ff32484a0a5.png)
  
### <a name="phase-3-optional-add-virtual-machines"></a><span data-ttu-id="041ab-306">Fase 3 (opcional): Agregue máquinas virtuales.</span><span class="sxs-lookup"><span data-stu-id="041ab-306">Phase 3 (Optional): Add virtual machines</span></span>

<span data-ttu-id="041ab-p127">Cree las máquinas virtuales que necesite en Azure. Para obtener más información, v[Creación de la primera máquina virtual de Windows en Azure Portal](https://go.microsoft.com/fwlink/p/?LinkId=393098).</span><span class="sxs-lookup"><span data-stu-id="041ab-p127">Create the virtual machines you need in Azure. For more information, see [Create your first Windows virtual machine in the Azure portal](https://go.microsoft.com/fwlink/p/?LinkId=393098).</span></span>
  
<span data-ttu-id="041ab-309">Use la configuración siguiente:</span><span class="sxs-lookup"><span data-stu-id="041ab-309">Use the following settings:</span></span>
  
- <span data-ttu-id="041ab-p128">En el panel **Datos básicos**, seleccione la misma suscripción y grupo de recursos que la red virtual. Registre el nombre de usuario y la contraseña en un lugar seguro. Los necesitará posteriormente para iniciar sesión en la máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="041ab-p128">On the **Basics** pane, select the same subscription and resource group as your virtual network. Record the user name and password in a secure location. You will need these later to sign in to the virtual machine.</span></span>
    
- <span data-ttu-id="041ab-313">En el panel **Tamaño**, elija el tamaño adecuado.</span><span class="sxs-lookup"><span data-stu-id="041ab-313">On the **Size** pane, choose the appropriate size.</span></span>
    
- <span data-ttu-id="041ab-p129">En el panel **Configuración**, en la sección **Almacenamiento**, seleccione el tipo de almacenamiento **Estándar** y la cuenta de almacenamiento configurada con su red virtual. En la sección **Red**, seleccione el nombre de la red virtual y la subred que van a hospedar las máquinas virtuales (no la subred de puerta de enlace). Deje todas las demás opciones con sus valores predeterminados.</span><span class="sxs-lookup"><span data-stu-id="041ab-p129">On the **Settings** pane, in the **Storage** section, select the **Standard** storage type and the storage account set up with your virtual network. In the **Network** section, select the name of your virtual network and the subnet for hosting virtual machines (not the GatewaySubnet). Leave all other settings at their default values.</span></span>
    
<span data-ttu-id="041ab-p130">Compruebe que la máquina virtual use DNS correctamente. Para ello, compruebe el DNS interno para asegurarse de que se agregaron registros de Dirección (A) a la nueva máquina virtual. Para tener acceso a Internet, las máquinas virtuales de Azure deben estar configuradas para usar el servidor proxy de la red local. Póngase en contacto con el administrador de red para informarse sobre los pasos de configuración adicionales que se deben realizar en el servidor.</span><span class="sxs-lookup"><span data-stu-id="041ab-p130">Verify that your virtual machine is using DNS correctly by checking your internal DNS to ensure that Address (A) records were added for you new virtual machine. To access the Internet, your Azure virtual machines must be configured to use your on-premises network's proxy server. Contact your network administrator for additional configuration steps to perform on the server.</span></span>
  
<span data-ttu-id="041ab-320">Esta es la configuración resultante.</span><span class="sxs-lookup"><span data-stu-id="041ab-320">Here is your resulting configuration.</span></span>
  
![La red virtual ahora hospeda máquinas virtuales que son accesibles desde la red local.](images/86ab63a6-bfae-4f75-8470-bd40dff123ac.png)
  
## <a name="next-step"></a><span data-ttu-id="041ab-322">Paso siguiente</span><span class="sxs-lookup"><span data-stu-id="041ab-322">Next step</span></span>
  
[<span data-ttu-id="041ab-323">Implementar Sincronización de directorios (DirSync) de Office 365 en Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="041ab-323">Deploy Office 365 Directory Synchronization (DirSync) in Microsoft Azure</span></span>](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md)
 


