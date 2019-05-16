---
title: Diseño de redes para IaaS de Microsoft Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 9cb70c9d-9ed9-47cc-af5a-6403d87d3372
description: 'Resumen: Aprenda a diseñar redes optimizadas para cargas de trabajo en IaaS de Microsoft Azure.'
ms.openlocfilehash: b06564c8a86c59dac4ac9a5380cd88cf9d045974
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068136"
---
# <a name="designing-networking-for-microsoft-azure-iaas"></a><span data-ttu-id="c3653-103">Diseño de redes para IaaS de Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="c3653-103">Designing networking for Microsoft Azure IaaS</span></span>

 <span data-ttu-id="c3653-104">**Resumen:** Comprenda cómo diseñar redes optimizadas para cargas de trabajo en IaaS de Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="c3653-104">**Summary:** Understand how to design optimized networking for workloads in Microsoft Azure IaaS.</span></span>
  
<span data-ttu-id="c3653-105">La optimización de las redes para las cargas de trabajo de TI hospedadas en IaaS de Azure requiere un conocimiento de las redes virtuales (VNets) de Azure, los espacios de direcciones, el enrutamiento, el DNS y el equilibrio de carga.</span><span class="sxs-lookup"><span data-stu-id="c3653-105">Optimizing networking for IT workloads hosted in Azure IaaS requires an understanding of Azure virtual networks (VNets), address spaces, routing, DNS, and load balancing.</span></span>
  
## <a name="planning-steps-for-any-vnet"></a><span data-ttu-id="c3653-106">Pasos de planeación para cualquier red virtual</span><span class="sxs-lookup"><span data-stu-id="c3653-106">Planning steps for any VNet</span></span>

<span data-ttu-id="c3653-107">Siga estos pasos para cualquier tipo de red virtual.</span><span class="sxs-lookup"><span data-stu-id="c3653-107">Follow these steps for any type of VNet.</span></span>
  
### <a name="step-1-prepare-your-intranet-for-microsoft-cloud-services"></a><span data-ttu-id="c3653-108">Paso 1: Preparar la intranet para los servicios en la nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c3653-108">Step 1: Prepare your intranet for Microsoft cloud services.</span></span>

<span data-ttu-id="c3653-109">Vea la sección **Pasos para preparar la red para Servicios en la nube de Microsoft** en [Elementos comunes de conectividad de Microsoft Cloud](common-elements-of-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="c3653-109">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
  
### <a name="step-2-optimize-your-internet-bandwidth"></a><span data-ttu-id="c3653-110">Paso 2: Optimizar el ancho de banda de Internet.</span><span class="sxs-lookup"><span data-stu-id="c3653-110">Step 2: Optimize your Internet bandwidth.</span></span>

<span data-ttu-id="c3653-111">Para optimizar el ancho de banda de Internet, siga los pasos 2 a 4 de la sección **Pasos para preparar la red para los servicios SaaS de Microsoft** del artículo [Diseño de redes para SaaS de Microsoft](designing-networking-for-microsoft-saas.md).</span><span class="sxs-lookup"><span data-stu-id="c3653-111">Optimize your Internet bandwidth using steps 2 - 4 of the **Steps to prepare your network for Microsoft SaaS services** section in [Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span></span>
  
### <a name="step-3-determine-the-type-of-vnet-cloud-only-or-cross-premises"></a><span data-ttu-id="c3653-112">Paso 3: Determinar el tipo de red virtual (solo nube o entre locales).</span><span class="sxs-lookup"><span data-stu-id="c3653-112">Step 3: Determine the type of VNet (cloud-only or cross-premises).</span></span>

<span data-ttu-id="c3653-p101">Una red virtual de solo nube no tiene conexión a una red local. Aquí le mostramos un ejemplo.</span><span class="sxs-lookup"><span data-stu-id="c3653-p101">A cloud-only VNet has no connection to an on-premises network. Here is an example.</span></span>
  
<span data-ttu-id="c3653-115">**Figura 1: Una red virtual de solo nube**</span><span class="sxs-lookup"><span data-stu-id="c3653-115">**Figure 1: A cloud-only VNet**</span></span>

![Figura 1: una red virtual de solo nube en Azure](media/8be19104-02b3-4a7f-b0a0-30d6fcf8890b.png)
  
<span data-ttu-id="c3653-117">La figura 1 muestra un conjunto de máquinas virtuales en una red virtual de solo nube.</span><span class="sxs-lookup"><span data-stu-id="c3653-117">Figure 1 shows a set of virtual machines in a cloud-only VNet.</span></span>
  
<span data-ttu-id="c3653-p102">Una red virtual entre locales tiene una conexión VPN de sitio a sitio (S2S) o de ExpressRoute a una red local a través de una puerta de enlace de Azure. Aquí le mostramos un ejemplo.</span><span class="sxs-lookup"><span data-stu-id="c3653-p102">A cross-premises VNet has a site-to-site (S2S) VPN or ExpressRoute connection to an on-premises network through an Azure gateway. Here is an example.</span></span>
  
<span data-ttu-id="c3653-120">**Figura 2: Una red virtual entre locales**</span><span class="sxs-lookup"><span data-stu-id="c3653-120">**Figure 2: A cross-premises VNet**</span></span>

![Figura 2: una red virtual entre locales en Azure](media/caacf007-e0dc-45d3-9531-441109776d25.png)
  
<span data-ttu-id="c3653-122">La figura 2 muestra un conjunto de máquinas virtuales en una red virtual entre locales, que está conectada a una red local.</span><span class="sxs-lookup"><span data-stu-id="c3653-122">Figure 2 shows a set of virtual machines in a cross-premises VNet, which is connected to an on-premises network.</span></span>
  
<span data-ttu-id="c3653-123">Consulte la sección adicional [Pasos de planeación para una red virtual entre locales](designing-networking-for-microsoft-azure-iaas.md#cross_prem) de este artículo.</span><span class="sxs-lookup"><span data-stu-id="c3653-123">See the additional [Planning steps for a cross-premises VNet](designing-networking-for-microsoft-azure-iaas.md#cross_prem) section in this article.</span></span>
  
### <a name="step-4-determine-the-address-space-of-the-vnet"></a><span data-ttu-id="c3653-124">Paso 4: Determinar el espacio de direcciones de la red virtual.</span><span class="sxs-lookup"><span data-stu-id="c3653-124">Step 4: Determine the address space of the VNet.</span></span>

<span data-ttu-id="c3653-125">La tabla 1 muestra los espacios de direcciones para los distintos tipos de redes virtuales.</span><span class="sxs-lookup"><span data-stu-id="c3653-125">Table 1 shows the address spaces for the different types of VNets.</span></span>
  
|<span data-ttu-id="c3653-126">**Tipo de red virtual**</span><span class="sxs-lookup"><span data-stu-id="c3653-126">**Type of VNet**</span></span>|<span data-ttu-id="c3653-127">**Espacio de direcciones de la red virtual**</span><span class="sxs-lookup"><span data-stu-id="c3653-127">**Virtual network address space**</span></span>|
|:-----|:-----|
|<span data-ttu-id="c3653-128">Solo de nube</span><span class="sxs-lookup"><span data-stu-id="c3653-128">Cloud-only</span></span>  <br/> |<span data-ttu-id="c3653-129">Espacio de direcciones privadas arbitrarias</span><span class="sxs-lookup"><span data-stu-id="c3653-129">Arbitrary private address space</span></span>  <br/> |
|<span data-ttu-id="c3653-130">Basada solo en la nube e interconectada</span><span class="sxs-lookup"><span data-stu-id="c3653-130">Interconnected cloud-only</span></span>  <br/> |<span data-ttu-id="c3653-131">Privado arbitrario, pero no se superpone con otras redes virtuales conectadas</span><span class="sxs-lookup"><span data-stu-id="c3653-131">Arbitrary private, but not overlapping with other connected VNets</span></span>  <br/> |
|<span data-ttu-id="c3653-132">Entre locales</span><span class="sxs-lookup"><span data-stu-id="c3653-132">Cross-premises</span></span>  <br/> |<span data-ttu-id="c3653-133">Privada, pero sin que se superponga con redes locales</span><span class="sxs-lookup"><span data-stu-id="c3653-133">Private, but not overlapping with on-premises</span></span>  <br/> |
|<span data-ttu-id="c3653-134">Local e interconectada</span><span class="sxs-lookup"><span data-stu-id="c3653-134">Interconnected cross-premises</span></span>  <br/> |<span data-ttu-id="c3653-135">Privada, pero sin que se superponga con otras redes locales y virtuales conectadas</span><span class="sxs-lookup"><span data-stu-id="c3653-135">Private, but not overlapping with on-premises and other connected VNets</span></span>  <br/> |
   
 <span data-ttu-id="c3653-136">**Tabla 1: Tipos de redes virtuales y el espacio de direcciones correspondiente**</span><span class="sxs-lookup"><span data-stu-id="c3653-136">**Table 1: Types of VNets and their corresponding address space**</span></span>
  
<span data-ttu-id="c3653-137">El DHCP asigna a las máquinas virtuales una configuración de direcciones desde el espacio de direcciones de la subred:</span><span class="sxs-lookup"><span data-stu-id="c3653-137">Virtual machines are assigned an address configuration from the address space of the subnet by DHCP:</span></span>
  
- <span data-ttu-id="c3653-138">Dirección/máscara de subred</span><span class="sxs-lookup"><span data-stu-id="c3653-138">Address/subnet mask</span></span>
    
- <span data-ttu-id="c3653-139">Puerta de enlace predeterminada</span><span class="sxs-lookup"><span data-stu-id="c3653-139">Default gateway</span></span>
    
- <span data-ttu-id="c3653-140">Direcciones IP del servidor DNS</span><span class="sxs-lookup"><span data-stu-id="c3653-140">DNS server IP addresses</span></span>
    
<span data-ttu-id="c3653-141">También puede reservar una dirección IP estática.</span><span class="sxs-lookup"><span data-stu-id="c3653-141">You can also reserve a static IP address.</span></span>
  
<span data-ttu-id="c3653-142">A las máquinas virtuales también se les puede asignar una dirección IP pública, ya sea individualmente o desde el servicio en la nube que las contiene (solo para máquinas de implementación clásicas).</span><span class="sxs-lookup"><span data-stu-id="c3653-142">Virtual machines can also be assigned a public IP address, either individually or from the containing cloud service (for classic deployment machines only).</span></span>
  
### <a name="step-5-determine-the-subnets-within-the-vnet-and-the-address-spaces-assigned-to-each"></a><span data-ttu-id="c3653-143">Paso 5: Determinar las subredes de la red virtual y los espacios de direcciones asignados a cada una.</span><span class="sxs-lookup"><span data-stu-id="c3653-143">Step 5: Determine the subnets within the VNet and the address spaces assigned to each.</span></span>

<span data-ttu-id="c3653-144">Hay dos tipos de subredes en una red virtual: una subred de puerta de enlace y una subred de hospedaje de máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="c3653-144">There are two types of subnets in a VNet, a gateway subnet and a virtual machine-hosting subnet.</span></span>
  
<span data-ttu-id="c3653-145">**Figura 3: Los dos tipos de subredes de Azure**</span><span class="sxs-lookup"><span data-stu-id="c3653-145">**Figure 3: The two types of subnets in Azure**</span></span>

![Figura 3: Los dos tipos de subredes de Azure](media/2eaa512d-1293-4e9b-b927-6bfe0fc0acb4.png)
  
<span data-ttu-id="c3653-147">La figura 3 muestra una VNet que contiene una subred de puerta de enlace que tiene una puerta de enlace de Azure y un conjunto de subredes de hospedaje de máquina virtual que contienen máquinas virtuales.</span><span class="sxs-lookup"><span data-stu-id="c3653-147">Figure 3 shows a VNet containing a gateway subnet that has an Azure gateway and a set of virtual machine-hosting subnets containing virtual machines.</span></span>
  
<span data-ttu-id="c3653-148">Azure necesita la subred de puerta de enlace de Azure para hospedar las dos máquinas virtuales de su puerta de enlace de Azure.</span><span class="sxs-lookup"><span data-stu-id="c3653-148">The Azure gateway subnet is needed by Azure to host the two virtual machines of your Azure gateway.</span></span> <span data-ttu-id="c3653-149">Especifique un espacio de direcciones que tenga una longitud de prefijo de, al menos, 29 bits (ejemplo: 192.168.15.248/29).</span><span class="sxs-lookup"><span data-stu-id="c3653-149">Specify an address space with at least a 29-bit prefix length (example: 192.168.15.248/29).</span></span> <span data-ttu-id="c3653-150">Se recomienda una longitud de prefijo de 27 bits o más pequeña, especialmente si está pensando en usar ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="c3653-150">A 27-bit or smaller prefix length is recommended, especially if you are planning to use ExpressRoute.</span></span>
  
<span data-ttu-id="c3653-151">Un procedimiento recomendado para determinar el espacio de direcciones de la subred de la puerta de enlace de Azure es:</span><span class="sxs-lookup"><span data-stu-id="c3653-151">A best practice for determining the address space of the Azure gateway subnet is:</span></span>
  
1. <span data-ttu-id="c3653-152">Decida el tamaño de la subred de puerta de enlace.</span><span class="sxs-lookup"><span data-stu-id="c3653-152">Decide on the size of the gateway subnet.</span></span>
    
2. <span data-ttu-id="c3653-153">En los bits variables del espacio de direcciones de la red virtual, establezca los bits usados para la subred de puerta de enlace en 0 y los bits restantes en 1.</span><span class="sxs-lookup"><span data-stu-id="c3653-153">In the variable bits in the address space of the VNet, set the bits used for the gateway subnet to 0 and set the remaining bits to 1.</span></span>
    
3. <span data-ttu-id="c3653-154">Convierta a decimales y expréselo como un espacio de direcciones con la longitud de prefijo establecida en el tamaño de la subred de puerta de enlace.</span><span class="sxs-lookup"><span data-stu-id="c3653-154">Convert to decimal and express as an address space with the prefix length set to the size of the gateway subnet.</span></span>
    
<span data-ttu-id="c3653-155">Con este método, el espacio de direcciones de la subred de puerta de enlace siempre está en el extremo más alejado del espacio de direcciones de la red virtual.</span><span class="sxs-lookup"><span data-stu-id="c3653-155">With this method, the address space for the gateway subnet is always at the farthest end of the VNet address space.</span></span>
  
<span data-ttu-id="c3653-p104">En este ejemplo, se define el prefijo de dirección que corresponde a la subred de puerta de enlace: el espacio de direcciones de la red virtual es 10.119.0.0/16. La organización usará inicialmente una conexión VPN de sitio a sitio, pero al final empleará ExpressRoute. La tabla 2 muestra los pasos y los resultados de determinar el prefijo de dirección de la subred de puerta de enlace en una notación de prefijos de red (también conocido como CIDR).</span><span class="sxs-lookup"><span data-stu-id="c3653-p104">Here is an example of defining the address prefix for the gateway subnet: The address space of the VNet is 10.119.0.0/16. The organization will initially use a site-to-site VPN connection, but will eventually get ExpressRoute. Table 2 shows the steps and results of determining the gateway subnet address prefix in network prefix notation (also known as CIDR).</span></span>

<span data-ttu-id="c3653-159">Estos son los pasos y el ejemplo de cómo determinar el prefijo de la dirección de subred de la puerta de enlace:</span><span class="sxs-lookup"><span data-stu-id="c3653-159">Here are the steps and example of determining the gateway subnet address prefix:</span></span>

1. <span data-ttu-id="c3653-160">Decida el tamaño de la subred de puerta de enlace.</span><span class="sxs-lookup"><span data-stu-id="c3653-160">Decide on the size of the gateway subnet.</span></span> <span data-ttu-id="c3653-161">Para nuestro ejemplo, elegimos/28.</span><span class="sxs-lookup"><span data-stu-id="c3653-161">For our example, we chose /28.</span></span>
2. <span data-ttu-id="c3653-162">Establezca los bits de la parte variable del espacio de direcciones de la red virtual (b) en 0 para los bits de subred de la puerta de enlace (G); en caso contrario, 1 (V).</span><span class="sxs-lookup"><span data-stu-id="c3653-162">Set the bits in the variable portion of the VNet address space (b) to 0 for the gateway subnet bits (G), otherwise 1 (V).</span></span> <span data-ttu-id="c3653-163">Para nuestro ejemplo, estamos usando el espacio de direcciones de 10.119.0.0/16 para la VNet.</span><span class="sxs-lookup"><span data-stu-id="c3653-163">For our example, we are using the 10.119.0.0/16 address space for the VNet.</span></span>
<br/>
<br/><span data-ttu-id="c3653-164">10,119.</span><span class="sxs-lookup"><span data-stu-id="c3653-164">10.119.</span></span> <span data-ttu-id="c3653-165">bbbbbbbb .</span><span class="sxs-lookup"><span data-stu-id="c3653-165">bbbbbbbb .</span></span> <span data-ttu-id="c3653-166">bbbbbbbb</span><span class="sxs-lookup"><span data-stu-id="c3653-166">bbbbbbbb</span></span>
<br/><span data-ttu-id="c3653-167">10,119.</span><span class="sxs-lookup"><span data-stu-id="c3653-167">10.119.</span></span> <span data-ttu-id="c3653-168">VVVVVVVV .</span><span class="sxs-lookup"><span data-stu-id="c3653-168">VVVVVVVV .</span></span> <span data-ttu-id="c3653-169">VVVVGGGG</span><span class="sxs-lookup"><span data-stu-id="c3653-169">VVVVGGGG</span></span>
<br/><span data-ttu-id="c3653-170">10,119.</span><span class="sxs-lookup"><span data-stu-id="c3653-170">10.119.</span></span> <span data-ttu-id="c3653-171">11111111.</span><span class="sxs-lookup"><span data-stu-id="c3653-171">11111111 .</span></span> <span data-ttu-id="c3653-172">11110000</span><span class="sxs-lookup"><span data-stu-id="c3653-172">11110000</span></span>
<br/><br/>
3. <span data-ttu-id="c3653-173">Convierta el resultado del paso 2 a decimal y Express como un espacio de direcciones.</span><span class="sxs-lookup"><span data-stu-id="c3653-173">Convert the result from step 2 to decimal and express as an address space.</span></span> <span data-ttu-id="c3653-174">En nuestro ejemplo, 10,119.</span><span class="sxs-lookup"><span data-stu-id="c3653-174">For our example, 10.119.</span></span> <span data-ttu-id="c3653-175">11111111.</span><span class="sxs-lookup"><span data-stu-id="c3653-175">11111111 .</span></span> <span data-ttu-id="c3653-176">11110000 es 10.119.255.240 y con la longitud de prefijo del paso 1 (28 en nuestro ejemplo), el prefijo de dirección de subred de la puerta de enlace resultante es 10.119.255.240/28.</span><span class="sxs-lookup"><span data-stu-id="c3653-176">11110000 is 10.119.255.240, and with the prefix length from step 1, (28 in our example), the resulting gateway subnet address prefix is 10.119.255.240/28.</span></span>
  
<span data-ttu-id="c3653-177">Para obtener más información, vea [calculadora de espacio de direcciones para subredes de puerta de enlace de Azure](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) .</span><span class="sxs-lookup"><span data-stu-id="c3653-177">See [Address space calculator for Azure gateway subnets](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) for more information.</span></span>
  
<span data-ttu-id="c3653-178">En las subredes de hospedaje de máquina virtual es donde se colocan las máquinas virtuales de Azure, lo cual se puede hacer siguiendo las instrucciones locales típicas, como un rol común o el nivel de una aplicación o para el aislamiento de la subred.</span><span class="sxs-lookup"><span data-stu-id="c3653-178">Virtual machine-hosting subnets are where you place Azure virtual machines, which you can do according to typical on-premises guidelines, such as a common role or tier of an application or for subnet isolation.</span></span>
  
<span data-ttu-id="c3653-179">Azure usa las tres primeras direcciones de cada subred.</span><span class="sxs-lookup"><span data-stu-id="c3653-179">Azure uses the first 3 addresses on each subnet.</span></span> <span data-ttu-id="c3653-180">Por lo tanto, el número de direcciones posibles en una subred de Azure es 2<sup>n</sup> -5, donde n es el número de bits de host.</span><span class="sxs-lookup"><span data-stu-id="c3653-180">Therefore, the number of possible addresses on an Azure subnet is 2<sup>n</sup> - 5, where n is the number of host bits.</span></span> <span data-ttu-id="c3653-181">La tabla 3 muestra la gama de máquinas virtuales y el número de bits de hosts necesarios, y el tamaño de la subred correspondiente.</span><span class="sxs-lookup"><span data-stu-id="c3653-181">Table 3 shows the range of virtual machines required, the number of hosts bits needed, and the corresponding subnet size.</span></span>
  
|<span data-ttu-id="c3653-182">**Máquinas virtuales requeridas**</span><span class="sxs-lookup"><span data-stu-id="c3653-182">**Virtual machines required**</span></span>|<span data-ttu-id="c3653-183">**Bits de host**</span><span class="sxs-lookup"><span data-stu-id="c3653-183">**Host bits**</span></span>|<span data-ttu-id="c3653-184">**Tamaño de la subred**</span><span class="sxs-lookup"><span data-stu-id="c3653-184">**Subnet size**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="c3653-185">1-3</span><span class="sxs-lookup"><span data-stu-id="c3653-185">1-3</span></span>  <br/> |<span data-ttu-id="c3653-186">3</span><span class="sxs-lookup"><span data-stu-id="c3653-186">3</span></span>  <br/> |<span data-ttu-id="c3653-187">/29</span><span class="sxs-lookup"><span data-stu-id="c3653-187">/29</span></span>  <br/> |
|<span data-ttu-id="c3653-188">4-11</span><span class="sxs-lookup"><span data-stu-id="c3653-188">4-11</span></span>  <br/> |<span data-ttu-id="c3653-189">4</span><span class="sxs-lookup"><span data-stu-id="c3653-189">4</span></span>  <br/> |<span data-ttu-id="c3653-190">/28</span><span class="sxs-lookup"><span data-stu-id="c3653-190">/28</span></span>  <br/> |
|<span data-ttu-id="c3653-191">12-27</span><span class="sxs-lookup"><span data-stu-id="c3653-191">12-27</span></span>  <br/> |<span data-ttu-id="c3653-192">2,5</span><span class="sxs-lookup"><span data-stu-id="c3653-192">5</span></span>  <br/> |<span data-ttu-id="c3653-193">/27</span><span class="sxs-lookup"><span data-stu-id="c3653-193">/27</span></span>  <br/> |
|<span data-ttu-id="c3653-194">28-59</span><span class="sxs-lookup"><span data-stu-id="c3653-194">28-59</span></span>  <br/> |<span data-ttu-id="c3653-195">6,5</span><span class="sxs-lookup"><span data-stu-id="c3653-195">6</span></span>  <br/> |<span data-ttu-id="c3653-196">/26</span><span class="sxs-lookup"><span data-stu-id="c3653-196">/26</span></span>  <br/> |
|<span data-ttu-id="c3653-197">60-123</span><span class="sxs-lookup"><span data-stu-id="c3653-197">60-123</span></span>  <br/> |<span data-ttu-id="c3653-198">0,7</span><span class="sxs-lookup"><span data-stu-id="c3653-198">7</span></span>  <br/> |<span data-ttu-id="c3653-199">/25</span><span class="sxs-lookup"><span data-stu-id="c3653-199">/25</span></span>  <br/> |
   
 <span data-ttu-id="c3653-200">**Tabla 3: Requisitos de la máquina virtual y tamaños de subred**</span><span class="sxs-lookup"><span data-stu-id="c3653-200">**Table 3: Virtual machine requirements and their subnet sizes**</span></span>
  
<span data-ttu-id="c3653-201">Para obtener más información acerca de la cantidad máxima de máquinas virtuales en una subred o VNet, consulte [límites de red](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span><span class="sxs-lookup"><span data-stu-id="c3653-201">For more information about the maximum amount of virtual machines on a subnet or VNet, see [Networking Limits](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span></span>
  
<span data-ttu-id="c3653-202">Para obtener más información, vea [planeación y diseño de redes virtuales de Azure](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/).</span><span class="sxs-lookup"><span data-stu-id="c3653-202">For more information, see [Plan and design Azure Virtual Networks](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/).</span></span>
  
### <a name="step-6-determine-the-dns-server-configuration-and-the-addresses-of-the-dns-servers-to-assign-to-vms-in-the-vnet"></a><span data-ttu-id="c3653-203">Paso 6: Determinar la configuración del servidor DNS y las direcciones de los servidores DNS para asignar a las máquinas virtuales en la red virtual.</span><span class="sxs-lookup"><span data-stu-id="c3653-203">Step 6: Determine the DNS server configuration and the addresses of the DNS servers to assign to VMs in the VNet.</span></span>

<span data-ttu-id="c3653-p112">Azure asigna a las máquinas virtuales las direcciones de los servidores DNS mediante DHCP. Los servidores DNS pueden suministrarlos:</span><span class="sxs-lookup"><span data-stu-id="c3653-p112">Azure assigns virtual machines the addresses of DNS servers by DHCP. DNS servers can be:</span></span>
  
- <span data-ttu-id="c3653-206">Azure: se proporciona un registro de nombres locales y una resolución de nombres de Internet</span><span class="sxs-lookup"><span data-stu-id="c3653-206">Supplied by Azure: Provides local name registration and local and Internet name resolution</span></span>
    
- <span data-ttu-id="c3653-207">Usted: se proporciona un registro de nombres locales o de intranet y una resolución de nombres de Internet o de intranet</span><span class="sxs-lookup"><span data-stu-id="c3653-207">Provided by you: Provides local or intranet name registration and either intranet or Internet name resolution</span></span>
    
<span data-ttu-id="c3653-208">En la tabla 4, se muestran las diferentes configuraciones de los servidores DNS para cada tipo de red virtual.</span><span class="sxs-lookup"><span data-stu-id="c3653-208">Table 4 shows the different configurations of DNS servers for each type of VNet.</span></span>
    
|<span data-ttu-id="c3653-209">**Tipo de red virtual**</span><span class="sxs-lookup"><span data-stu-id="c3653-209">**Type of VNet**</span></span>|<span data-ttu-id="c3653-210">**Servidor DNS**</span><span class="sxs-lookup"><span data-stu-id="c3653-210">**DNS server**</span></span>|
|:-----|:-----|
|<span data-ttu-id="c3653-211">Solo de nube</span><span class="sxs-lookup"><span data-stu-id="c3653-211">Cloud-only</span></span>  <br/> |<span data-ttu-id="c3653-212">Suministrado por Azure para la resolución de nombres de Internet y locales</span><span class="sxs-lookup"><span data-stu-id="c3653-212">Azure-supplied for local and Internet name resolution</span></span>  <br/> <span data-ttu-id="c3653-213">Máquina virtual de Azure para la resolución de nombres de Internet y locales (reenvío DNS)</span><span class="sxs-lookup"><span data-stu-id="c3653-213">Azure virtual machine for local and Internet name resolution (DNS forwarding)</span></span>  <br/> |
|<span data-ttu-id="c3653-214">Entre locales</span><span class="sxs-lookup"><span data-stu-id="c3653-214">Cross-premises</span></span>  <br/> |<span data-ttu-id="c3653-215">Local para la resolución de nombres locales y de intranet</span><span class="sxs-lookup"><span data-stu-id="c3653-215">On-premises for local and intranet name resolution</span></span>  <br/> <span data-ttu-id="c3653-216">Máquina virtual de Azure para la resolución de nombres de Internet y locales (replicación y reenvío DNS)</span><span class="sxs-lookup"><span data-stu-id="c3653-216">Azure virtual machine for local and intranet name resolution (DNS replication and forwarding)</span></span>  <br/> |
   
 <span data-ttu-id="c3653-217">**Tabla 4: Opciones del servidor DNS para los dos tipos diferentes de redes virtuales**</span><span class="sxs-lookup"><span data-stu-id="c3653-217">**Table 4: DNS server options for the two different types of VNets**</span></span>
  
<span data-ttu-id="c3653-218">Para obtener más información, vea [resolución de nombres para máquinas virtuales e instancias de rol](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances).</span><span class="sxs-lookup"><span data-stu-id="c3653-218">For more information, see [Name Resolution for VMs and Role Instances](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances).</span></span>
  
### <a name="step-7-determine-the-load-balancing-configuration-internet-facing-or-internal"></a><span data-ttu-id="c3653-219">Paso 7: Determinar la configuración de equilibrio de carga (accesible desde Internet o interna).</span><span class="sxs-lookup"><span data-stu-id="c3653-219">Step 7: Determine the load balancing configuration (Internet-facing or internal).</span></span>

<span data-ttu-id="c3653-p113">En algunos casos, queremos distribuir el tráfico entrante a un conjunto de servidores que tienen el mismo rol. IaaS de Azure dispone de una instalación integrada para hacer esto con cargas de tráfico accesibles desde Internet e internas.</span><span class="sxs-lookup"><span data-stu-id="c3653-p113">In some cases, you want to distribute incoming traffic to a set of servers that have the same role. Azure IaaS has a built-in facility to do this for Internet-facing and internal traffic loads.</span></span>
  
<span data-ttu-id="c3653-222">El equilibrio de carga de Azure accesible desde Internet distribuye aleatoriamente el tráfico entrante no solicitado de Internet a los miembros de un conjunto de carga equilibrada. </span><span class="sxs-lookup"><span data-stu-id="c3653-222">Azure Internet-facing load balancing randomly distributes unsolicited incoming traffic from the Internet to the members of a load-balanced set.</span></span>
  
<span data-ttu-id="c3653-223">**Figura 4: Un equilibrador de carga externo en Azure**</span><span class="sxs-lookup"><span data-stu-id="c3653-223">**Figure 4: An external load balancer in Azure**</span></span>

![Figura 4: Un equilibrador de carga externo en Azure](media/eb5945e5-0c2b-40f1-b9ed-54bb2b0f9e59.png)
  
<span data-ttu-id="c3653-225">La figura 4 muestra un equilibrador de carga externo en Azure que distribuye el tráfico entrante en una regla de NAT de entrada o un punto de conexión a un conjunto de máquinas virtuales en un conjunto de carga equilibrada.</span><span class="sxs-lookup"><span data-stu-id="c3653-225">Figure 4 shows an external load balancer in Azure that distributes incoming traffic on an inbound NAT rule or endpoint to a set of virtual machines in a load-balanced set.</span></span>
  
<span data-ttu-id="c3653-226">El equilibrio de carga interno de Azure distribuye aleatoriamente el tráfico entrante no solicitado desde otras máquinas virtuales de Azure o desde equipos de la intranet a los miembros de un conjunto de equilibrio de carga. </span><span class="sxs-lookup"><span data-stu-id="c3653-226">Azure internal load balancing randomly distributes unsolicited incoming traffic from other Azure VMs or from intranet computers to the members of a load-balanced set.</span></span> 
  
<span data-ttu-id="c3653-227">**Figura 5: Un equilibrador de carga interno en Azure**</span><span class="sxs-lookup"><span data-stu-id="c3653-227">**Figure 5: An internal load balancer in Azure**</span></span>

![Figura 5: Un equilibrador de carga interno en Azure](media/d1451b73-6465-449d-b3e6-22160ce51f35.png)
  
<span data-ttu-id="c3653-229">La figura 5 muestra un equilibrador de carga interno en Azure que distribuye el tráfico entrante en una regla de NAT de entrada o un punto de conexión a un conjunto de máquinas virtuales en un conjunto de carga equilibrada.</span><span class="sxs-lookup"><span data-stu-id="c3653-229">Figure 5 shows an internal load balancer in Azure that distributes incoming traffic on an inbound NAT rule or endpoint to a set of virtual machines in a load-balanced set.</span></span>
  
<span data-ttu-id="c3653-230">Para obtener más información, vea equilibrador de [carga de Azure](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview).</span><span class="sxs-lookup"><span data-stu-id="c3653-230">For more information, see [Azure Load Balancer](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview).</span></span>
  
### <a name="step-8-determine-the-use-of-virtual-appliances-and-user-defined-routes"></a><span data-ttu-id="c3653-231">Paso 8: Determinar el uso de las aplicaciones virtuales y las rutas definidas por el usuario.</span><span class="sxs-lookup"><span data-stu-id="c3653-231">Step 8: Determine the use of virtual appliances and user-defined routes.</span></span>

<span data-ttu-id="c3653-232">Si tiene que reenviar el tráfico a aplicaciones virtuales de la red virtual, puede que deba agregar a una subred una o varias rutas que haya definido el usuario.</span><span class="sxs-lookup"><span data-stu-id="c3653-232">If you need to forward traffic to virtual appliances in your VNet, you may need to add one or more user-defined routes to a subnet.</span></span>
  
<span data-ttu-id="c3653-233">**Figura 6: Las aplicaciones virtuales y las rutas definidas por el usuario en Azure**</span><span class="sxs-lookup"><span data-stu-id="c3653-233">**Figure 6: Virtual appliances and user-defined routes in Azure**</span></span>

![Figura 6: Las aplicaciones virtuales y las rutas definidas por el usuario en Azure](media/f181d0f4-ebf9-439e-9c98-dec17428c32b.png)
  
<span data-ttu-id="c3653-235">La figura 6 muestra una red virtual entre locales y una ruta definida por el usuario asignada a una subred de hospedaje de máquina virtual que apunta a una aplicación virtual.</span><span class="sxs-lookup"><span data-stu-id="c3653-235">Figure 6 shows a cross-premises VNet and a user-defined route assigned to a virtual machine-hosting subnet that points to a virtual appliance.</span></span>
  
<span data-ttu-id="c3653-236">Para obtener más información, vea [rutas definidas por el usuario y el reenvío IP](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview).</span><span class="sxs-lookup"><span data-stu-id="c3653-236">For more information, see [User Defined Routes and IP Forwarding](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview).</span></span>
  
### <a name="step-9-determine-how-computers-from-the-internet-will-connect-to-virtual-machines"></a><span data-ttu-id="c3653-237">Paso 9: Determinar cómo se conectarán los equipos de Internet a las máquinas virtuales.</span><span class="sxs-lookup"><span data-stu-id="c3653-237">Step 9: Determine how computers from the Internet will connect to virtual machines.</span></span>

<span data-ttu-id="c3653-238">Hay varias maneras de proporcionar acceso a Internet a las máquinas virtuales de una red virtual, que incluye el acceso desde la red de la organización a través del servidor proxy u otro dispositivo perimetral.</span><span class="sxs-lookup"><span data-stu-id="c3653-238">There are multiple ways to provide Internet access to the virtual machines on a VNet, which includes access from your organization network through your proxy server or other edge device.</span></span>
  
<span data-ttu-id="c3653-239">La tabla 5 recoge los métodos para filtrar o inspeccionar el tráfico entrante no solicitado.</span><span class="sxs-lookup"><span data-stu-id="c3653-239">Table 5 lists the methods for filtering or inspecting unsolicited incoming traffic.</span></span>
  
|<span data-ttu-id="c3653-240">**Método**</span><span class="sxs-lookup"><span data-stu-id="c3653-240">**Method**</span></span>|<span data-ttu-id="c3653-241">**Modelo de implementación**</span><span class="sxs-lookup"><span data-stu-id="c3653-241">**Deployment model**</span></span>|
|:-----|:-----|
|<span data-ttu-id="c3653-242">1. Puntos de conexión y ACL configurados en los servicios en la nube</span><span class="sxs-lookup"><span data-stu-id="c3653-242">1. Endpoints and ACLs configured on cloud services</span></span>  <br/> |<span data-ttu-id="c3653-243">SICA</span><span class="sxs-lookup"><span data-stu-id="c3653-243">Classic</span></span>  <br/> |
|<span data-ttu-id="c3653-244">2. Grupos de seguridad de red</span><span class="sxs-lookup"><span data-stu-id="c3653-244">2. Network security groups</span></span>  <br/> |<span data-ttu-id="c3653-245">Administrador de recursos y clásico</span><span class="sxs-lookup"><span data-stu-id="c3653-245">Resource Manager and classic</span></span>  <br/> |
|<span data-ttu-id="c3653-246">3. Equilibrador de carga accesible desde Internet con reglas de NAT entrantes</span><span class="sxs-lookup"><span data-stu-id="c3653-246">3. Internet-facing load balancer with inbound NAT rules</span></span>  <br/> |<span data-ttu-id="c3653-247">Administrador de recursos</span><span class="sxs-lookup"><span data-stu-id="c3653-247">Resource Manager</span></span>  <br/> |
|<span data-ttu-id="c3653-248">4. dispositivos de seguridad de red en Azure Marketplace (no se muestra)</span><span class="sxs-lookup"><span data-stu-id="c3653-248">4. Network security appliances in the Azure Marketplace (not shown)</span></span>  <br/> |<span data-ttu-id="c3653-249">Administrador de recursos y clásico</span><span class="sxs-lookup"><span data-stu-id="c3653-249">Resource Manager and classic</span></span>  <br/> |
   
 <span data-ttu-id="c3653-250">**Tabla 5: Métodos de conexión a máquinas virtuales y sus correspondientes modelos de implementación de Azure**</span><span class="sxs-lookup"><span data-stu-id="c3653-250">**Table 5: Methods of connecting to virtual machines and their corresponding Azure deployment models**</span></span>
  
<span data-ttu-id="c3653-251">**Figura 7: Conexión a máquinas virtuales de Azure a través de Internet**</span><span class="sxs-lookup"><span data-stu-id="c3653-251">**Figure 7: Connecting to Azure virtual machines over the Internet**</span></span>

![Figura 7: Conexión a máquinas virtuales de Azure a través de Internet](media/c5e3531b-170a-4482-a6ff-fb8fbbe81b35.png)
  
<span data-ttu-id="c3653-253">La figura 7 muestra un equipo conectado a Internet que se conecta a una máquina virtual en un servicio en la nube usando un punto de conexión, una máquina virtual de una subred que usa un grupo de seguridad de red y una máquina virtual de una subred que usa un equilibrador de carga externo y reglas de NAT entrantes.</span><span class="sxs-lookup"><span data-stu-id="c3653-253">Figure 7 shows an Internet-connected computer connecting to a virtual machine in a cloud service using an endpoint, a virtual machine on a subnet using a network security group, and a virtual machine on a subnet using an external load balancer and inbound NAT rules.</span></span>
  
<span data-ttu-id="c3653-254">La seguridad adicional la proporcionan:</span><span class="sxs-lookup"><span data-stu-id="c3653-254">Additional security is provided by:</span></span>
  
- <span data-ttu-id="c3653-255">Conexiones de Escritorio remoto y SSH, que se autentican y se cifran.</span><span class="sxs-lookup"><span data-stu-id="c3653-255">Remote Desktop and SSH connections, which are authenticated and encrypted.</span></span>
    
- <span data-ttu-id="c3653-256">Sesiones remotas de PowerShell, que se autentican y se cifran.</span><span class="sxs-lookup"><span data-stu-id="c3653-256">Remote PowerShell sessions, which are authenticated and encrypted.</span></span>
    
- <span data-ttu-id="c3653-257">Modo de transporte IPsec, que puede usar para el cifrado de extremo a extremo.</span><span class="sxs-lookup"><span data-stu-id="c3653-257">IPsec transport mode, which you can use for end-to-end encryption.</span></span>
    
- <span data-ttu-id="c3653-258">Protección DDoS de Azure, que ayuda a prevenir ataques internos y externos</span><span class="sxs-lookup"><span data-stu-id="c3653-258">Azure DDOS protection, which helps prevent external and internal attacks</span></span>
    
<span data-ttu-id="c3653-259">Para obtener más información, consulte [seguridad en la nube de Microsoft para arquitectos de empresa](https://aka.ms/cloudarchsecurity) y [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span><span class="sxs-lookup"><span data-stu-id="c3653-259">For more information, see [Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity) and [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span></span>
  
### <a name="step-10-for-multiple-vnets-determine-the-vnet-to-vnet-connection-topology"></a><span data-ttu-id="c3653-260">Paso 10: Para varias redes virtuales, determinar la topología de conexión de una red virtual a otra.</span><span class="sxs-lookup"><span data-stu-id="c3653-260">Step 10: For multiple VNets, determine the VNet-to-VNet connection topology.</span></span>

<span data-ttu-id="c3653-261">Las redes virtuales pueden conectarse entre sí mediante topologías como las que se usan para conectar los sitios de una organización.</span><span class="sxs-lookup"><span data-stu-id="c3653-261">VNets can be connected to each other using topologies similar to those used for connecting the sites of an organization.</span></span>
  
<span data-ttu-id="c3653-262">Una configuración de encadenamiento conecta las redes virtuales de una serie.</span><span class="sxs-lookup"><span data-stu-id="c3653-262">A daisy chain configuration connects the VNets in a series.</span></span>
  
<span data-ttu-id="c3653-263">**Figura 8: Una configuración de encadenamiento para redes virtuales**</span><span class="sxs-lookup"><span data-stu-id="c3653-263">**Figure 8: A daisy-chained configuration for VNets**</span></span>

![Figura 8: una configuración de encadenamiento para redes virtuales de Azure](media/264d5dd4-06c5-483f-9428-a18cc1f68ac1.png)
  
<span data-ttu-id="c3653-265">La figura 8 muestra cinco redes virtuales conectadas en serie con una configuración de encadenamiento.</span><span class="sxs-lookup"><span data-stu-id="c3653-265">Figure 8 shows five VNets connected in series using a daisy-chained configuration.</span></span>
  
<span data-ttu-id="c3653-266">Una configuración de concentrador y radio conecta varias redes virtuales a un conjunto de redes virtuales centrales, que están conectadas entre sí.</span><span class="sxs-lookup"><span data-stu-id="c3653-266">A spoke and hub configuration connects multiple VNets to a set of central VNets, which are themselves connected to each other.</span></span>
  
<span data-ttu-id="c3653-267">**Figura 9: Una configuración de concentrador y radio para redes virtuales**</span><span class="sxs-lookup"><span data-stu-id="c3653-267">**Figure 9: A spoke and hub configuration for VNets**</span></span>

![Figura 9: una configuración de concentrador y radio para redes virtuales de Azure](media/dd442a38-5b76-4ac5-b743-8fc7711a91ba.png)
  
<span data-ttu-id="c3653-269">La figura 9 muestra seis redes virtuales, dos redes virtuales son concentradores conectados entre sí y también otras dos son redes virtuales de radio.</span><span class="sxs-lookup"><span data-stu-id="c3653-269">Figure 9 shows six VNets, two VNets are hubs that are connected to each other and also two other spoke VNets.</span></span>
  
<span data-ttu-id="c3653-270">Una configuración de malla completa conecta las redes virtuales entre sí.</span><span class="sxs-lookup"><span data-stu-id="c3653-270">A full mesh configuration connects every VNet to each other.</span></span>
  
<span data-ttu-id="c3653-271">**Figura 10: Una configuración de malla completa para redes virtuales**</span><span class="sxs-lookup"><span data-stu-id="c3653-271">**Figure 10: A full mesh configuration for VNets**</span></span>

![Figura 10: una configuración de malla para redes virtuales de Azure](media/9dda0738-10db-4a63-95b3-79851a399b71.png)
  
<span data-ttu-id="c3653-273">La figura 10 muestra cuatro redes virtuales que están conectadas entre sí y que usan un total de seis conexiones de red virtual a red virtual.</span><span class="sxs-lookup"><span data-stu-id="c3653-273">Figure 10 shows four VNets that are all connected to each other, using a total of six VNet-to-VNet connections.</span></span>
  
## <a name="planning-steps-for-a-cross-premises-vnet"></a><span data-ttu-id="c3653-274">Pasos de planeación para una red virtual entre locales</span><span class="sxs-lookup"><span data-stu-id="c3653-274">Planning steps for a cross-premises VNet</span></span>
<span data-ttu-id="c3653-275"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="c3653-275"></span></span>

<span data-ttu-id="c3653-276">Siga estos pasos para una red virtual entre locales.</span><span class="sxs-lookup"><span data-stu-id="c3653-276">Follow these steps for a cross-premises VNet.</span></span>
  
> [!TIP]
> <span data-ttu-id="c3653-277">Para crear un entorno de prueba y desarrollo simulado entre locales, vea [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span><span class="sxs-lookup"><span data-stu-id="c3653-277">To create a simulated cross-premises dev/test environment, see [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span></span> 
  
### <a name="step-1-determine-the-cross-premises-connection-to-the-vnet-s2s-vpn-or-expressroute"></a><span data-ttu-id="c3653-278">Paso 1: Determinar la conexión entre locales a la red virtual (VPN S2S o ExpressRoute).</span><span class="sxs-lookup"><span data-stu-id="c3653-278">Step 1: Determine the cross-premises connection to the VNet (S2S VPN or ExpressRoute).</span></span>

<span data-ttu-id="c3653-279">En la tabla 6 se recogen los distintos tipos de conexiones.</span><span class="sxs-lookup"><span data-stu-id="c3653-279">Table 6 lists the different types of connections.</span></span>
  
|<span data-ttu-id="c3653-280">**Tipo de conexión**</span><span class="sxs-lookup"><span data-stu-id="c3653-280">**Type of connection**</span></span>|<span data-ttu-id="c3653-281">**Finalidad**</span><span class="sxs-lookup"><span data-stu-id="c3653-281">**Purpose**</span></span>|
|:-----|:-----|
|<span data-ttu-id="c3653-282">VPN sitio a sitio (S2S)</span><span class="sxs-lookup"><span data-stu-id="c3653-282">Site-to-Site (S2S) VPN</span></span>  <br/> |<span data-ttu-id="c3653-283">Conecte los sitios de 1-10 (incluidas otras redes virtuales) a una única VNet.</span><span class="sxs-lookup"><span data-stu-id="c3653-283">Connect 1-10 sites (including other VNets) to a single VNet.</span></span>  <br/> |
|<span data-ttu-id="c3653-284">ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="c3653-284">ExpressRoute</span></span>  <br/> |<span data-ttu-id="c3653-285">Un vínculo seguro y privado a Azure a través de un proveedor de intercambio de Internet (IXP) o un proveedor de servicio de red (NSP).</span><span class="sxs-lookup"><span data-stu-id="c3653-285">A private, secure link to Azure via an Internet Exchange Provider (IXP) or a Network Service Provider (NSP).</span></span>  <br/> |
|<span data-ttu-id="c3653-286">VPN punto a sitio (P2S)</span><span class="sxs-lookup"><span data-stu-id="c3653-286">Point-to-Site (P2S) VPN</span></span>  <br/> |<span data-ttu-id="c3653-287">Conecta un solo equipo a una red virtual.</span><span class="sxs-lookup"><span data-stu-id="c3653-287">Connects a single computer to a VNet.</span></span>  <br/> |
|<span data-ttu-id="c3653-288">Dispositivos VPN para el emparejamiento de VNET o de red virtual a red virtual (V2V) </span><span class="sxs-lookup"><span data-stu-id="c3653-288">VNet peering or VNet-to-VNet (V2V) VPN</span></span>  <br/> |<span data-ttu-id="c3653-289">Conecta una red virtual a otra.</span><span class="sxs-lookup"><span data-stu-id="c3653-289">Connects a VNet to another VNet.</span></span>  <br/> |
   
 <span data-ttu-id="c3653-290">**Tabla 6: Los tipos de conexiones para redes virtuales entre locales**</span><span class="sxs-lookup"><span data-stu-id="c3653-290">**Table 6: The types of connections for cross-premises VNets**</span></span>
  
<span data-ttu-id="c3653-291">Para obtener más información sobre el número máximo de conexiones, consulte [límites de red](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span><span class="sxs-lookup"><span data-stu-id="c3653-291">For more information on the maximum number of connections, see [Networking Limits](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span></span>
  
<span data-ttu-id="c3653-292">Para obtener más información acerca de los dispositivos VPN, vea [dispositivos VPN para conexiones de red virtual de sitio a sitio](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span><span class="sxs-lookup"><span data-stu-id="c3653-292">For more information about VPN devices, see [VPN devices for site-to-site virtual network connections](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="c3653-293">Para obtener más información sobre el emparejamiento de VNet, consulte [emparejamiento de Vnet](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview).</span><span class="sxs-lookup"><span data-stu-id="c3653-293">For more information about VNet peering, see [VNet peering](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview).</span></span>
  
<span data-ttu-id="c3653-294">**Figura 11: Las cuatro maneras de conectarse a una red virtual entre locales**</span><span class="sxs-lookup"><span data-stu-id="c3653-294">**Figure 11: The four ways to connect to a cross-premises VNet**</span></span>

![Figura 11: las tres maneras de conectarse a una red virtual de Azure entre locales](media/d5d4a625-cfbd-4a77-9159-eaca69d07e93.png)
  
<span data-ttu-id="c3653-296">La figura 11 muestra una red virtual con los cuatro tipos de conexiones: una conexión de P2S de un equipo, una conexión VPN S2S desde una red local, una conexión de ExpressRoute desde una red local y una conexión de red virtual a red virtual desde otra red virtual.</span><span class="sxs-lookup"><span data-stu-id="c3653-296">Figure 11 shows a VNet with the four types of connections: a P2S connection from a computer, an S2S VPN connection from an on-premises network, an ExpressRoute connection from an on-premises network, and a VNet-to-VNet connection from another VNet.</span></span> 
  
<span data-ttu-id="c3653-297">Puede conectarse a las máquinas virtuales de una red virtual de las maneras siguientes:</span><span class="sxs-lookup"><span data-stu-id="c3653-297">You can connect to VMs in a VNet in the following ways:</span></span>
  
- <span data-ttu-id="c3653-298">Administración de máquinas virtuales de redes virtuales desde la red local o Internet</span><span class="sxs-lookup"><span data-stu-id="c3653-298">Administration of VNet VMs from your on-premises network or the Internet</span></span>
    
- <span data-ttu-id="c3653-299">Acceso a cargas de trabajo de TI desde la red local</span><span class="sxs-lookup"><span data-stu-id="c3653-299">IT workload access from your on-premises network</span></span>
    
- <span data-ttu-id="c3653-300">Ampliación de la red a través de redes virtuales adicionales</span><span class="sxs-lookup"><span data-stu-id="c3653-300">Extension of your network through additional VNets</span></span>
    
<span data-ttu-id="c3653-301">La seguridad en las conexiones se consigue mediante lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="c3653-301">Security for connections is provided by the following:</span></span>
  
- <span data-ttu-id="c3653-302">P2S usa el protocolo de túnel de sockets de seguros (SSTP) </span><span class="sxs-lookup"><span data-stu-id="c3653-302">P2S uses the Secure Socket Tunneling Protocol (SSTP)</span></span> 
    
- <span data-ttu-id="c3653-303">S2S y conexiones VPN de red virtual a red virtual usan el modo de túnel IPsec con AES256</span><span class="sxs-lookup"><span data-stu-id="c3653-303">S2S and VNet-to-VNet VPN connections use IPsec tunnel mode with AES256</span></span>
    
- <span data-ttu-id="c3653-304">ExpressRoute es una conexión WAN privada</span><span class="sxs-lookup"><span data-stu-id="c3653-304">ExpressRoute is a private WAN connection</span></span>
    
<span data-ttu-id="c3653-305">Para obtener más información, consulte [seguridad en la nube de Microsoft para arquitectos de empresa](https://aka.ms/cloudarchsecurity) y [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span><span class="sxs-lookup"><span data-stu-id="c3653-305">For more information, see [Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity) and [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span></span>
  
### <a name="step-2-determine-the-on-premises-vpn-device-or-router"></a><span data-ttu-id="c3653-306">Paso 2: Determinar el dispositivo o enrutador VPN local.</span><span class="sxs-lookup"><span data-stu-id="c3653-306">Step 2: Determine the on-premises VPN device or router.</span></span>

<span data-ttu-id="c3653-307">El dispositivo o enrutador VPN local actúa como:</span><span class="sxs-lookup"><span data-stu-id="c3653-307">Your on-premises VPN device or router acts as:</span></span>
  
- <span data-ttu-id="c3653-308">Par IPsec que finaliza la conexión de VPN S2S desde la puerta de enlace de Azure.</span><span class="sxs-lookup"><span data-stu-id="c3653-308">An IPsec peer, terminating the S2S VPN connection from the Azure gateway.</span></span>
    
- <span data-ttu-id="c3653-309">Par BPG y punto de finalización para la conexión de ExpressRoute de emparejamiento privado.</span><span class="sxs-lookup"><span data-stu-id="c3653-309">The BPG peer and termination point for the private peering ExpressRoute connection.</span></span>
    
<span data-ttu-id="c3653-310">**Figura 12: El dispositivo o enrutador de VPN local**</span><span class="sxs-lookup"><span data-stu-id="c3653-310">**Figure 12: The on-premises VPN router or device**</span></span>

![Figura 12: El dispositivo o enrutador de VPN local](media/bd221468-a660-4730-aa55-0426986480b9.png)
  
<span data-ttu-id="c3653-312">La figura 12 muestra una red virtual entre locales conectada a un enrutador o dispositivo VPN local.</span><span class="sxs-lookup"><span data-stu-id="c3653-312">Figure 12 shows a cross-premises VNet connected to an on-premises VPN router or device.</span></span>
  
<span data-ttu-id="c3653-313">Para obtener más información, vea [acerca de la puerta de enlace VPN](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways).</span><span class="sxs-lookup"><span data-stu-id="c3653-313">For more information, see [About VPN gateway](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways).</span></span>
  
### <a name="step-3-add-routes-to-your-intranet-to-make-the-address-space-of-the-vnet-reachable"></a><span data-ttu-id="c3653-314">Paso 3: agregar rutas a la intranet para que el espacio de direcciones de la red virtual sea accesible.</span><span class="sxs-lookup"><span data-stu-id="c3653-314">Step 3: Add routes to your intranet to make the address space of the VNet reachable.</span></span>

<span data-ttu-id="c3653-315">El enrutamiento a redes virtuales desde ubicaciones locales consiste en lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="c3653-315">Routing to VNets from on-premises consists of the following:</span></span>
  
1. <span data-ttu-id="c3653-316">Una ruta para el espacio de direcciones de red virtual que apunte al dispositivo VPN.</span><span class="sxs-lookup"><span data-stu-id="c3653-316">A route for the VNet address space that points toward your VPN device.</span></span>
    
2. <span data-ttu-id="c3653-317">Una ruta para el espacio de direcciones de red virtual en el dispositivo VPN que apunte a la conexión VPN S2S o de ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="c3653-317">A route for the VNet address space on your VPN device that points across the S2S VPN or ExpressRoute connection</span></span>
    
<span data-ttu-id="c3653-318">**Figura 13: Las rutas locales necesarias para hacer que una red virtual sea accesible**</span><span class="sxs-lookup"><span data-stu-id="c3653-318">**Figure 13: The on-premises routes needed to make a VNet reachable**</span></span>

![Figura 13: las rutas locales necesarias para hacer que una red virtual de Azure sea accesible](media/7a1e20c1-fbc4-4cb9-9961-735da4e23307.png)
  
<span data-ttu-id="c3653-320">En la figura 13, se muestra la información de enrutamiento que necesitan los enrutadores locales y el enrutador o dispositivo VPN que representa el espacio de direcciones de la red virtual.</span><span class="sxs-lookup"><span data-stu-id="c3653-320">Figure 13 shows the routing information needed by the on-premises routers and the VPN router or device that represents the address space of the VNet.</span></span>
  
### <a name="step-4-for-expressroute-plan-for-the-new-connection-with-your-provider"></a><span data-ttu-id="c3653-321">Paso 4: Para ExpressRoute, planear la nueva conexión con el proveedor.</span><span class="sxs-lookup"><span data-stu-id="c3653-321">Step 4: For ExpressRoute, plan for the new connection with your provider.</span></span>

<span data-ttu-id="c3653-322">Puede crear una conexión de ExpressRoute con emparejamiento privado entre la red local y la nube de Microsoft de tres maneras diferentes:</span><span class="sxs-lookup"><span data-stu-id="c3653-322">You can create an ExpressRoute connection with private peering between your on-premises network and the Microsoft cloud in three different ways:</span></span>
  
- <span data-ttu-id="c3653-323">Colocalizada en un intercambio en la nube</span><span class="sxs-lookup"><span data-stu-id="c3653-323">Co-located at a cloud exchange</span></span>
    
- <span data-ttu-id="c3653-324">Conexiones Ethernet de punto a punto</span><span class="sxs-lookup"><span data-stu-id="c3653-324">Point-to-point Ethernet connections</span></span>
    
- <span data-ttu-id="c3653-325">Redes (IP VPN) universales</span><span class="sxs-lookup"><span data-stu-id="c3653-325">Any-to-any (IP VPN) networks</span></span>
    
<span data-ttu-id="c3653-326">**Figura 14: Uso de ExpressRoute para conectarse a una red virtual entre locales**</span><span class="sxs-lookup"><span data-stu-id="c3653-326">**Figure 14: Using ExpressRoute to connect to a cross-premises VNet**</span></span>

![Figura 14: uso de ExpressRoute para conectarse a una red virtual de Azure entre locales](media/7030bd39-69a6-4283-8567-3434e1ab6ba6.png)
  
<span data-ttu-id="c3653-328">La figura 14 muestra una red virtual entre locales y una conexión de ExpressRoute de un enrutador local a Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="c3653-328">Figure 14 shows a cross-premises VNet and an ExpressRoute connection from an on-premises router to Microsoft Azure.</span></span>
  
<span data-ttu-id="c3653-329">Para obtener más información, consulte [ExpressRoute para la conectividad en la nube de Microsoft](expressroute-for-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="c3653-329">For more information, see [ExpressRoute for Microsoft cloud connectivity](expressroute-for-microsoft-cloud-connectivity.md).</span></span>
  
### <a name="step-5-determine-the-local-network-address-space-for-the-azure-gateway"></a><span data-ttu-id="c3653-330">Paso 5: Determinar el espacio de direcciones de red local para la puerta de enlace de Azure.</span><span class="sxs-lookup"><span data-stu-id="c3653-330">Step 5: Determine the Local Network address space for the Azure gateway.</span></span>

<span data-ttu-id="c3653-331">Para el enrutamiento a una red local u otras redes virtuales desde una red virtual, Azure reenvía el tráfico a través de una puerta de enlace de Azure que coincide con el espacio de direcciones de red local asignado a la puerta de enlace.</span><span class="sxs-lookup"><span data-stu-id="c3653-331">For the routing to on-premises or other VNets from a VNet, Azure forwards traffic across an Azure gateway that matches the Local Network address space assigned to the gateway.</span></span>
  
<span data-ttu-id="c3653-332">**Figura 15: El espacio de direcciones de red local para una red virtual entre locales**</span><span class="sxs-lookup"><span data-stu-id="c3653-332">**Figure 15: The Local Network address space for a cross-premises VNet**</span></span>

![Figura 15: el espacio de direcciones de red local para una red virtual de Azure entre locales](media/e3af2652-8b8e-4551-9a0b-b550e6e7e3c0.png)
  
<span data-ttu-id="c3653-334">La figura 15 muestra una red virtual entre locales y el espacio de direcciones de red local en la puerta de enlace de Azure, que representa el espacio de direcciones accesible en la red local. </span><span class="sxs-lookup"><span data-stu-id="c3653-334">Figure 15 shows a cross-premises VNet and the Local Network address space on the Azure gateway, which represents the reachable address space on the on-premises network.</span></span> 
  
<span data-ttu-id="c3653-335">Puede definir el espacio de direcciones de red local de las siguientes formas:</span><span class="sxs-lookup"><span data-stu-id="c3653-335">You can define the Local Network address space in these ways:</span></span>
  
- <span data-ttu-id="c3653-336">Opción 1: La lista de prefijos del espacio de direcciones que se necesita actualmente o que está en uso (podría ser necesario actualizar al agregar nuevas subredes).</span><span class="sxs-lookup"><span data-stu-id="c3653-336">Option 1: The list of prefixes for the address space currently needed or in use (updates might be needed when you add new subnets).</span></span>
    
- <span data-ttu-id="c3653-337">Opción 2: El espacio de direcciones local completo (solo es necesario actualizar cuando se agrega un espacio de direcciones nuevo).</span><span class="sxs-lookup"><span data-stu-id="c3653-337">Option 2: Your entire on-premises address space (updates only needed when you add new address space).</span></span>
    
<span data-ttu-id="c3653-338">Como la puerta de enlace de Azure no permite rutas resumidas, debe definir el espacio de direcciones de red local para la opción 2 de modo que no incluya el espacio de direcciones de red virtual.</span><span class="sxs-lookup"><span data-stu-id="c3653-338">Because the Azure gateway does not allow summarized routes, you must define the Local Network address space for option 2 so that it does not include the VNet address space.</span></span>
  
<span data-ttu-id="c3653-339">**Figura 16: El orificio del espacio de direcciones que crea el espacio de direcciones de red virtual**</span><span class="sxs-lookup"><span data-stu-id="c3653-339">**Figure 16: The address space hole created by the VNet address space**</span></span>

![Figura 16: el orificio del espacio de direcciones que crea el espacio de direcciones de la red virtual](media/e79c4840-f9e3-4741-9b72-59db6043aefa.png)
  
<span data-ttu-id="c3653-341">La figura 16 muestra una representación de un espacio de direcciones con el espacio raíz y el espacio de direcciones de red virtual.</span><span class="sxs-lookup"><span data-stu-id="c3653-341">Figure 16 shows a representation of an address space, with the root space and the VNet address space.</span></span>
  
<span data-ttu-id="c3653-342">A continuación, se muestra un ejemplo de cómo definir los prefijos para el espacio de direcciones de red local alrededor del espacio de direcciones "agujero" creado por la red virtual:</span><span class="sxs-lookup"><span data-stu-id="c3653-342">Here is an example of defining the prefixes for the Local Network address space around the address space "hole" created by the VNet:</span></span>
  
- <span data-ttu-id="c3653-p114">Una organización usa partes del espacio de direcciones privadas (10.0.0.0/8, 172.16.0.0/12 y 192.168.0.0/16) a través de su red local. Eligió la opción 2 y 10.100.100.0/24 como espacio de direcciones de red virtual.</span><span class="sxs-lookup"><span data-stu-id="c3653-p114">An organization uses portions of the private address space (10.0.0.0/8, 172.16.0.0/12, and 192.168.0.0/16) across their on-premises network. They chose option 2 and 10.100.100.0/24 as their VNet address space.</span></span>
    
<span data-ttu-id="c3653-345">La tabla 7 muestra los pasos y prefijos resultantes que definen el espacio de direcciones de red local en este ejemplo.</span><span class="sxs-lookup"><span data-stu-id="c3653-345">Table 7 shows the steps and resulting prefixes that define the Local Network address space for this example.</span></span>
  
|<span data-ttu-id="c3653-346">**Paso**</span><span class="sxs-lookup"><span data-stu-id="c3653-346">**Step**</span></span>|<span data-ttu-id="c3653-347">**Resultados**</span><span class="sxs-lookup"><span data-stu-id="c3653-347">**Results**</span></span>|
|:-----|:-----|
|<span data-ttu-id="c3653-348">1. Mostrar los prefijos que no son el espacio raíz para el espacio de direcciones de red virtual.</span><span class="sxs-lookup"><span data-stu-id="c3653-348">1. List the prefixes that are not the root space for the VNet address space.</span></span>  <br/> |<span data-ttu-id="c3653-349">172.16.0.0/12 y 192.168.0.0/16</span><span class="sxs-lookup"><span data-stu-id="c3653-349">172.16.0.0/12 and 192.168.0.0/16</span></span>  <br/> |
|<span data-ttu-id="c3653-350">2. enumerar los prefijos que no se superponen para los octetos variables hasta el último octeto usado en el espacio de direcciones de red virtual, pero sin incluirlo.</span><span class="sxs-lookup"><span data-stu-id="c3653-350">2. List the non-overlapping prefixes for variable octets up to but not including the last used octet in the VNet address space.</span></span>  <br/> |<span data-ttu-id="c3653-351">10.0.0.0/16, 10.1.0.0/16... 10.99.0.0/16, 10.101.0.0/16... 10.254.0.0/16, 10.255.0.0/16 (255 prefijos, omitir 10.100.0.0/16)</span><span class="sxs-lookup"><span data-stu-id="c3653-351">10.0.0.0/16, 10.1.0.0/16…10.99.0.0/16, 10.101.0.0/16…10.254.0.0/16, 10.255.0.0/16 (255 prefixes, skipping 10.100.0.0/16)</span></span>  <br/> |
|<span data-ttu-id="c3653-352">3. enumerar los prefijos que no se superponen en el último octeto usado del espacio de direcciones de la red virtual.</span><span class="sxs-lookup"><span data-stu-id="c3653-352">3. List the non-overlapping prefixes within the last used octet of the VNet address space.</span></span>  <br/> |<span data-ttu-id="c3653-353">10.100.0.0/24, 10.100.1.0/24... 10.100.99.0/24, 10.100.101.0/24... 10.100.254.0/24, 10.100.0.255.0/24 (255 prefijos, omitir 10.100.100.0/24)</span><span class="sxs-lookup"><span data-stu-id="c3653-353">10.100.0.0/24, 10.100.1.0/24…10.100.99.0/24, 10.100.101.0/24…10.100.254.0/24, 10.100.0.255.0/24 (255 prefixes, skipping 10.100.100.0/24)</span></span>  <br/> |
   
 <span data-ttu-id="c3653-354">**Tabla 7: Ejemplo de espacio de red de dirección local**</span><span class="sxs-lookup"><span data-stu-id="c3653-354">**Table 7: Example Local Address network space**</span></span>
  
### <a name="step-6-configure-on-premises-dns-servers-for-dns-replication-with-dns-servers-hosted-in-azure"></a><span data-ttu-id="c3653-355">Paso 6: Configurar los servidores DNS locales para la replicación DNS con servidores DNS hospedados en Azure.</span><span class="sxs-lookup"><span data-stu-id="c3653-355">Step 6: Configure on-premises DNS servers for DNS replication with DNS servers hosted in Azure.</span></span>

<span data-ttu-id="c3653-356">Para garantizar que los equipos locales puedan resolver los nombres de los servidores basados en Azure y que estos servidores puedan resolver los nombres de los equipos locales, configure:</span><span class="sxs-lookup"><span data-stu-id="c3653-356">To ensure that on-premises computers can resolve the names of Azure-based servers and Azure-based servers can resolve the names of on-premises computers, configure:</span></span>
  
- <span data-ttu-id="c3653-357">Los servidores DNS de la red virtual para que reenvíen a los servidores DNS locales</span><span class="sxs-lookup"><span data-stu-id="c3653-357">The DNS servers in your VNet to forward to on-premises DNS servers</span></span>
    
- <span data-ttu-id="c3653-358">La replicación DNS de las zonas apropiadas entre servidores DNS locales y en la red virtual</span><span class="sxs-lookup"><span data-stu-id="c3653-358">DNS replication of the appropriate zones between DNS servers on-premises and in the VNet</span></span>
    
<span data-ttu-id="c3653-359">**Figura 17: Reenvío y replicación DNS de un servidor DNS en una red virtual entre locales**</span><span class="sxs-lookup"><span data-stu-id="c3653-359">**Figure 17: DNS replication and forwarding for a DNS server in a cross-premises VNet**</span></span>

![Figura 17: reenvío y replicación DNS de un servidor DNS en una red virtual de Azure entre locales](media/ab55e5ce-ccb0-49d4-a301-657a727f97b2.png)
  
<span data-ttu-id="c3653-p115">La figura 17 muestra una red virtual entre locales con servidores DNS en la red local y en una subred de la red virtual. El reenvío y la replicación de DNS se han configurado entre los dos servidores DNS.</span><span class="sxs-lookup"><span data-stu-id="c3653-p115">Figure 17 shows a cross-premises VNet with DNS servers in the on-premises network and on a subnet in the VNet. DNS replication and forwarding has been configured between the two DNS servers.</span></span>
  
### <a name="step-7-determine-the-use-of-forced-tunneling"></a><span data-ttu-id="c3653-363">Paso 7: Determinar el uso de la tunelización forzada.</span><span class="sxs-lookup"><span data-stu-id="c3653-363">Step 7: Determine the use of forced tunneling.</span></span>

<span data-ttu-id="c3653-364">La ruta predeterminada del sistema para las subredes de Azure apunta a Internet.</span><span class="sxs-lookup"><span data-stu-id="c3653-364">The default system route for Azure subnets points to the Internet.</span></span> <span data-ttu-id="c3653-365">Para asegurarse de que todo el tráfico de las máquinas virtuales se recorre a través de la conexión entre locales, cree una tabla de enrutamiento con la ruta predeterminada que use la puerta de enlace de Azure como su dirección de próximo salto.</span><span class="sxs-lookup"><span data-stu-id="c3653-365">To ensure that all traffic from virtual machines travels across the cross-premises connection, create a routing table with the default route that uses the Azure gateway as its next-hop address.</span></span> <span data-ttu-id="c3653-366">A continuación, asocie la tabla de rutas con la subred.</span><span class="sxs-lookup"><span data-stu-id="c3653-366">You then associate the route table with the subnet.</span></span> <span data-ttu-id="c3653-367">Esto se conoce como tunelización forzada.</span><span class="sxs-lookup"><span data-stu-id="c3653-367">This is known as forced tunneling.</span></span> <span data-ttu-id="c3653-368">Para obtener más información, consulte [configurar túneles forzados](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm).</span><span class="sxs-lookup"><span data-stu-id="c3653-368">For more information, see [Configure forced tunneling](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm).</span></span>
  
<span data-ttu-id="c3653-369">**Figura 18: Rutas definidas por el usuario y tunelización forzada en una red virtual entre locales**</span><span class="sxs-lookup"><span data-stu-id="c3653-369">**Figure 18: User-defined routes and forced tunneling for a cross-premises VNet**</span></span>

![Figura 18: rutas definidas por el usuario y tunelización forzada para una red virtual de Azure entre locales](media/1e545ec6-c2d9-48d2-bb5e-e0a581fee004.png)
  
<span data-ttu-id="c3653-371">La figura 18 muestra una red virtual entre locales con una ruta definida por el usuario para una subred que apunta a la puerta de enlace de Azure.</span><span class="sxs-lookup"><span data-stu-id="c3653-371">Figure 18 shows a cross-premises VNet with a user-defined route for a subnet pointing to the Azure gateway.</span></span>
  
## <a name="sharepoint-server-2016-farm-in-azure"></a><span data-ttu-id="c3653-372">Granja de servidores de SharePoint Server 2016 en Azure</span><span class="sxs-lookup"><span data-stu-id="c3653-372">SharePoint Server 2016 farm in Azure</span></span>
<span data-ttu-id="c3653-373"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="c3653-373"></span></span>

<span data-ttu-id="c3653-374">Un ejemplo de una carga de trabajo de TI de intranet hospedada en IaaS de Azure es una granja de servidores de SharePoint Server 2016 de varios niveles y altamente disponible.</span><span class="sxs-lookup"><span data-stu-id="c3653-374">An example of an intranet IT workload hosted in Azure IaaS is a highly-available, multi-tier SharePoint Server 2016 farm.</span></span>
  
<span data-ttu-id="c3653-375">**Figura 19: Una granja de SharePoint Server 2016 de la intranet y de alta disponibilidad en IaaS de Azure**</span><span class="sxs-lookup"><span data-stu-id="c3653-375">**Figure 19: A highly-available intranet SharePoint Server 2016 farm in Azure IaaS**</span></span>

![Una granja de servidores de alta disponibilidad de SharePoint Server 2016 en IaaS de Azure](media/3a922e21-df91-455f-ba90-78abdd48d98d.png)
  
<span data-ttu-id="c3653-377">La figura 19 muestra los nueve servidores de una granja de servidores de SharePoint Server 2016 implementada en una red virtual entre locales que usa equilibradores de carga internos para los niveles front-end y de datos.</span><span class="sxs-lookup"><span data-stu-id="c3653-377">Figure 19 shows the nine servers of a SharePoint Server 2016 farm deployed in a cross-premises VNet that uses internal load balancers for the front-end and data tiers.</span></span> <span data-ttu-id="c3653-378">Para obtener más información, incluidas las instrucciones paso a paso para la implementación y el diseño, vea [SharePoint Server 2016 en Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure).</span><span class="sxs-lookup"><span data-stu-id="c3653-378">For more information, including step-by-step design and deployment instructions, see [SharePoint Server 2016 in Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure).</span></span>
  
> [!TIP]
> <span data-ttu-id="c3653-379">Para crear una granja de servidores de SharePoint Server 2016 de un solo servidor en una red virtual entre locales simulada, vea [intranet SharePoint server 2016 en el entorno de prueba y desarrollo de Azure](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment).</span><span class="sxs-lookup"><span data-stu-id="c3653-379">To create a single-server SharePoint Server 2016 farm in a simulated cross-premises VNet, see [Intranet SharePoint Server 2016 in Azure dev/test environment](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment).</span></span> 
  
<span data-ttu-id="c3653-380">Para obtener ejemplos adicionales de cargas de trabajo de ti implementadas en máquinas virtuales en una red virtual de Azure entre locales, vea [escenarios de nube híbrida para IaaS de Azure](https://docs.microsoft.com/office365/enterprise/hybrid-cloud-scenarios-for-azure-iaas).</span><span class="sxs-lookup"><span data-stu-id="c3653-380">For additional examples of IT workloads deployed on virtual machines in a cross-premises Azure virtual network, see [Hybrid cloud scenarios for Azure IaaS](https://docs.microsoft.com/office365/enterprise/hybrid-cloud-scenarios-for-azure-iaas).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c3653-381">Ver también</span><span class="sxs-lookup"><span data-stu-id="c3653-381">See also</span></span>

[<span data-ttu-id="c3653-382">Microsoft Cloud Networking para arquitectos profesionales</span><span class="sxs-lookup"><span data-stu-id="c3653-382">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="c3653-383">Recursos de arquitectura de TI de Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="c3653-383">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)


