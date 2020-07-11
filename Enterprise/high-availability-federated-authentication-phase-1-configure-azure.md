---
title: Fase 1 de la autenticación federada de alta disponibilidad configurar Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Solutions
ms.assetid: 91266aac-4d00-4b5f-b424-86a1a837792c
description: 'Resumen: configure la infraestructura de Microsoft Azure para hospedar la autenticación federada de alta disponibilidad para Microsoft 365.'
ms.openlocfilehash: 5b0eed42076a79af52566868c8e6134c48fd847f
ms.sourcegitcommit: d8ca7017b25d5ddc2771e662e02b62ff2058383b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2020
ms.locfileid: "45102548"
---
# <a name="high-availability-federated-authentication-phase-1-configure-azure"></a><span data-ttu-id="baf8c-103">Fase 1 de la autenticación federada de alta disponibilidad: Configurar Azure</span><span class="sxs-lookup"><span data-stu-id="baf8c-103">High availability federated authentication Phase 1: Configure Azure</span></span>

<span data-ttu-id="baf8c-104">En esta fase, se crean los grupos de recursos, la red virtual (VNet) y los conjuntos de disponibilidad en Azure que hospedarán las máquinas virtuales en las fases 2, 3 y 4.</span><span class="sxs-lookup"><span data-stu-id="baf8c-104">In this phase, you create the resource groups, virtual network (VNet), and availability sets in Azure that will host the virtual machines in phases 2, 3, and 4.</span></span> <span data-ttu-id="baf8c-105">Debe completar esta fase para poder pasar a la [Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="baf8c-105">You must complete this phase before moving on to [Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md).</span></span> <span data-ttu-id="baf8c-106">Consulte [implementar la autenticación federada de alta disponibilidad para Microsoft 365 en Azure en](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) todas las fases.</span><span class="sxs-lookup"><span data-stu-id="baf8c-106">See [Deploy high availability federated authentication for Microsoft 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
<span data-ttu-id="baf8c-107">Azure debe estar aprovisionado con estos componentes básicos:</span><span class="sxs-lookup"><span data-stu-id="baf8c-107">Azure must be provisioned with these basic components:</span></span>
  
- <span data-ttu-id="baf8c-108">Grupos de recursos</span><span class="sxs-lookup"><span data-stu-id="baf8c-108">Resource groups</span></span>
    
- <span data-ttu-id="baf8c-109">Una red virtual (VNET) de Azure entre locales con subredes para hospedar las máquinas virtuales de Azure</span><span class="sxs-lookup"><span data-stu-id="baf8c-109">A cross-premises Azure virtual network (VNet) with subnets for hosting the Azure virtual machines</span></span>
    
- <span data-ttu-id="baf8c-110">Grupos de seguridad de red para realizar el aislamiento de subredes</span><span class="sxs-lookup"><span data-stu-id="baf8c-110">Network security groups for performing subnet isolation</span></span>
    
- <span data-ttu-id="baf8c-111">Conjuntos de disponibilidad</span><span class="sxs-lookup"><span data-stu-id="baf8c-111">Availability sets</span></span>
    
## <a name="configure-azure-components"></a><span data-ttu-id="baf8c-112">Configurar componentes de Azure</span><span class="sxs-lookup"><span data-stu-id="baf8c-112">Configure Azure components</span></span>

<span data-ttu-id="baf8c-113">Antes de empezar a configurar los componentes de Azure, rellene las tablas siguientes.</span><span class="sxs-lookup"><span data-stu-id="baf8c-113">Before you begin configuring Azure components, fill in the following tables.</span></span> <span data-ttu-id="baf8c-114">Para ayudarle en los procedimientos de configuración de Azure, imprima esta sección y anote la información necesaria, o bien copie esta sección en un documento y rellénelo.</span><span class="sxs-lookup"><span data-stu-id="baf8c-114">To assist you in the procedures for configuring Azure, print this section and write down the needed information or copy this section to a document and fill it in.</span></span> <span data-ttu-id="baf8c-115">Para la configuración de la red virtual, rellene la tabla V.</span><span class="sxs-lookup"><span data-stu-id="baf8c-115">For the settings of the VNet, fill in Table V.</span></span>
  
|<span data-ttu-id="baf8c-116">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="baf8c-116">**Item**</span></span>|<span data-ttu-id="baf8c-117">**Opción de configuración**</span><span class="sxs-lookup"><span data-stu-id="baf8c-117">**Configuration setting**</span></span>|<span data-ttu-id="baf8c-118">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="baf8c-118">**Description**</span></span>|<span data-ttu-id="baf8c-119">**Valor**</span><span class="sxs-lookup"><span data-stu-id="baf8c-119">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="baf8c-120">1.</span><span class="sxs-lookup"><span data-stu-id="baf8c-120">1.</span></span>  <br/> |<span data-ttu-id="baf8c-121">Nombre de VNET</span><span class="sxs-lookup"><span data-stu-id="baf8c-121">VNet name</span></span>  <br/> |<span data-ttu-id="baf8c-122">Nombre que se asignará a la red virtual (por ejemplo, FedAuthNet).</span><span class="sxs-lookup"><span data-stu-id="baf8c-122">A name to assign to the VNet (example FedAuthNet).</span></span>  <br/> |![línea](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="baf8c-124">2.</span><span class="sxs-lookup"><span data-stu-id="baf8c-124">2.</span></span>  <br/> |<span data-ttu-id="baf8c-125">Ubicación de la VNET</span><span class="sxs-lookup"><span data-stu-id="baf8c-125">VNet location</span></span>  <br/> |<span data-ttu-id="baf8c-126">Centro de datos regional de Azure que contendrá la red virtual.</span><span class="sxs-lookup"><span data-stu-id="baf8c-126">The regional Azure datacenter that will contain the virtual network.</span></span>  <br/> |![línea](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="baf8c-128">3.</span><span class="sxs-lookup"><span data-stu-id="baf8c-128">3.</span></span>  <br/> |<span data-ttu-id="baf8c-129">Dirección IP del dispositivo VPN</span><span class="sxs-lookup"><span data-stu-id="baf8c-129">VPN device IP address</span></span>  <br/> |<span data-ttu-id="baf8c-130">Dirección IPv4 pública de la interfaz del dispositivo VPN en Internet.</span><span class="sxs-lookup"><span data-stu-id="baf8c-130">The public IPv4 address of your VPN device's interface on the Internet.</span></span>  <br/> |![línea](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="baf8c-132">4.</span><span class="sxs-lookup"><span data-stu-id="baf8c-132">4.</span></span>  <br/> |<span data-ttu-id="baf8c-133">Espacio de direcciones de la VNET</span><span class="sxs-lookup"><span data-stu-id="baf8c-133">VNet address space</span></span>  <br/> |<span data-ttu-id="baf8c-134">The address space for the virtual network.</span><span class="sxs-lookup"><span data-stu-id="baf8c-134">The address space for the virtual network.</span></span> <span data-ttu-id="baf8c-135">Work with your IT department to determine this address space.</span><span class="sxs-lookup"><span data-stu-id="baf8c-135">Work with your IT department to determine this address space.</span></span>  <br/> |![línea](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="baf8c-137">5.</span><span class="sxs-lookup"><span data-stu-id="baf8c-137">5.</span></span>  <br/> |<span data-ttu-id="baf8c-138">Clave compartida IPsec</span><span class="sxs-lookup"><span data-stu-id="baf8c-138">IPsec shared key</span></span>  <br/> |<span data-ttu-id="baf8c-139">A 32-character random, alphanumeric string that will be used to authenticate both sides of the site-to-site VPN connection.</span><span class="sxs-lookup"><span data-stu-id="baf8c-139">A 32-character random, alphanumeric string that will be used to authenticate both sides of the site-to-site VPN connection.</span></span> <span data-ttu-id="baf8c-140">Work with your IT or security department to determine this key value.</span><span class="sxs-lookup"><span data-stu-id="baf8c-140">Work with your IT or security department to determine this key value.</span></span> <span data-ttu-id="baf8c-141">Alternately, see [Create a random string for an IPsec preshared key](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).</span><span class="sxs-lookup"><span data-stu-id="baf8c-141">Alternately, see [Create a random string for an IPsec preshared key](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).</span></span>  <br/> |![línea](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="baf8c-143">**Tabla V: Configuración de la red virtual entre locales**</span><span class="sxs-lookup"><span data-stu-id="baf8c-143">**Table V: Cross-premises virtual network configuration**</span></span>
  
<span data-ttu-id="baf8c-144">Next, fill in Table S for the subnets of this solution.</span><span class="sxs-lookup"><span data-stu-id="baf8c-144">Next, fill in Table S for the subnets of this solution.</span></span> <span data-ttu-id="baf8c-145">All address spaces should be in Classless Interdomain Routing (CIDR) format, also known as network prefix format.</span><span class="sxs-lookup"><span data-stu-id="baf8c-145">All address spaces should be in Classless Interdomain Routing (CIDR) format, also known as network prefix format.</span></span> <span data-ttu-id="baf8c-146">An example is 10.24.64.0/20.</span><span class="sxs-lookup"><span data-stu-id="baf8c-146">An example is 10.24.64.0/20.</span></span>
  
<span data-ttu-id="baf8c-147">For the first three subnets, specify a name and a single IP address space based on the virtual network address space.</span><span class="sxs-lookup"><span data-stu-id="baf8c-147">For the first three subnets, specify a name and a single IP address space based on the virtual network address space.</span></span> <span data-ttu-id="baf8c-148">For the gateway subnet, determine the 27-bit address space (with a /27 prefix length) for the Azure gateway subnet with the following:</span><span class="sxs-lookup"><span data-stu-id="baf8c-148">For the gateway subnet, determine the 27-bit address space (with a /27 prefix length) for the Azure gateway subnet with the following:</span></span>
  
1. <span data-ttu-id="baf8c-149">Establezca los bits variables en el espacio de direcciones de la VNET en 1, hasta los bits usados por la subred de la puerta de enlace y, después, establezca el resto de los bits en 0.</span><span class="sxs-lookup"><span data-stu-id="baf8c-149">Set the variable bits in the address space of the VNet to 1, up to the bits being used by the gateway subnet, then set the remaining bits to 0.</span></span>
    
2. <span data-ttu-id="baf8c-150">Convierta los bits resultantes a decimales y expréselo como un espacio de direcciones con la longitud de prefijo establecida en el tamaño de la subred de puerta de enlace.</span><span class="sxs-lookup"><span data-stu-id="baf8c-150">Convert the resulting bits to decimal and express it as an address space with the prefix length set to the size of the gateway subnet.</span></span>
    
<span data-ttu-id="baf8c-151">Vea [calculadora de espacio de direcciones para subredes de puerta de enlace de Azure](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) para obtener un bloque de comandos de PowerShell y una aplicación de consola de C# o Python que realice este cálculo.</span><span class="sxs-lookup"><span data-stu-id="baf8c-151">See [Address space calculator for Azure gateway subnets](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) for a PowerShell command block and C# or Python console application that performs this calculation for you.</span></span>
  
<span data-ttu-id="baf8c-152">Trabaje con su departamento de TI para determinar estos espacios de direcciones a partir del espacio de direcciones de la red virtual.</span><span class="sxs-lookup"><span data-stu-id="baf8c-152">Work with your IT department to determine these address spaces from the virtual network address space.</span></span>
  
|<span data-ttu-id="baf8c-153">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="baf8c-153">**Item**</span></span>|<span data-ttu-id="baf8c-154">**Nombre de la subred**</span><span class="sxs-lookup"><span data-stu-id="baf8c-154">**Subnet name**</span></span>|<span data-ttu-id="baf8c-155">**Espacio de direcciones de la subred**</span><span class="sxs-lookup"><span data-stu-id="baf8c-155">**Subnet address space**</span></span>|<span data-ttu-id="baf8c-156">**Finalidad**</span><span class="sxs-lookup"><span data-stu-id="baf8c-156">**Purpose**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="baf8c-157">1.</span><span class="sxs-lookup"><span data-stu-id="baf8c-157">1.</span></span>  <br/> |![línea](./media/Common-Images/TableLine.png)  <br/> |![línea](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="baf8c-160">La subred usada por el controlador de dominio de Active Directory Domain Services (AD DS) y las máquinas virtuales (VM) del servidor de sincronización de directorios.</span><span class="sxs-lookup"><span data-stu-id="baf8c-160">The subnet used by the Active Directory Domain Services (AD DS) domain controller and directory synchronization server virtual machines (VMs).</span></span>  <br/> |
|<span data-ttu-id="baf8c-161">2.</span><span class="sxs-lookup"><span data-stu-id="baf8c-161">2.</span></span>  <br/> |![línea](./media/Common-Images/TableLine.png)  <br/> |![línea](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="baf8c-164">Subred usada por las máquinas virtuales de AD FS.</span><span class="sxs-lookup"><span data-stu-id="baf8c-164">The subnet used by the AD FS VMs.</span></span>  <br/> |
|<span data-ttu-id="baf8c-165">3.</span><span class="sxs-lookup"><span data-stu-id="baf8c-165">3.</span></span>  <br/> |![línea](./media/Common-Images/TableLine.png)  <br/> |![línea](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="baf8c-168">Subred usada por las máquinas virtuales del proxy de aplicación web.</span><span class="sxs-lookup"><span data-stu-id="baf8c-168">The subnet used by the web application proxy VMs.</span></span>  <br/> |
|<span data-ttu-id="baf8c-169">4.</span><span class="sxs-lookup"><span data-stu-id="baf8c-169">4.</span></span>  <br/> |<span data-ttu-id="baf8c-170">GatewaySubnet</span><span class="sxs-lookup"><span data-stu-id="baf8c-170">GatewaySubnet</span></span>  <br/> |![línea](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="baf8c-172">Subred usada por las máquinas virtuales de la puerta de enlace de Azure.</span><span class="sxs-lookup"><span data-stu-id="baf8c-172">The subnet used by the Azure gateway VMs.</span></span>  <br/> |
   
 <span data-ttu-id="baf8c-173">**Tabla S: Subredes de la red virtual**</span><span class="sxs-lookup"><span data-stu-id="baf8c-173">**Table S: Subnets in the virtual network**</span></span>
  
<span data-ttu-id="baf8c-174">Ahora, rellene la Tabla I para las direcciones IP estáticas asignadas a las máquinas virtuales y a las instancias del equilibrador de carga.</span><span class="sxs-lookup"><span data-stu-id="baf8c-174">Next, fill in Table I for the static IP addresses assigned to virtual machines and load balancer instances.</span></span>
  
|<span data-ttu-id="baf8c-175">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="baf8c-175">**Item**</span></span>|<span data-ttu-id="baf8c-176">**Objetivo**</span><span class="sxs-lookup"><span data-stu-id="baf8c-176">**Purpose**</span></span>|<span data-ttu-id="baf8c-177">**Dirección IP en la subred**</span><span class="sxs-lookup"><span data-stu-id="baf8c-177">**IP address on the subnet**</span></span>|<span data-ttu-id="baf8c-178">**Valor**</span><span class="sxs-lookup"><span data-stu-id="baf8c-178">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="baf8c-179">1.</span><span class="sxs-lookup"><span data-stu-id="baf8c-179">1.</span></span>  <br/> |<span data-ttu-id="baf8c-180">Dirección IP estática del primer controlador de dominio</span><span class="sxs-lookup"><span data-stu-id="baf8c-180">Static IP address of the first domain controller</span></span>  <br/> |<span data-ttu-id="baf8c-181">La cuarta dirección IP posible del espacio de direcciones de la subred definida en el elemento 1 de la Tabla S.</span><span class="sxs-lookup"><span data-stu-id="baf8c-181">The fourth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |![línea](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="baf8c-183">2.</span><span class="sxs-lookup"><span data-stu-id="baf8c-183">2.</span></span>  <br/> |<span data-ttu-id="baf8c-184">Dirección IP estática del segundo controlador de dominio</span><span class="sxs-lookup"><span data-stu-id="baf8c-184">Static IP address of the second domain controller</span></span>  <br/> |<span data-ttu-id="baf8c-185">La quinta dirección IP posible del espacio de direcciones de la subred definida en el elemento 1 de la Tabla S.</span><span class="sxs-lookup"><span data-stu-id="baf8c-185">The fifth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |![línea](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="baf8c-187">3.</span><span class="sxs-lookup"><span data-stu-id="baf8c-187">3.</span></span>  <br/> |<span data-ttu-id="baf8c-188">Dirección IP estática del servidor de sincronización de directorios</span><span class="sxs-lookup"><span data-stu-id="baf8c-188">Static IP address of the directory synchronization server</span></span>  <br/> |<span data-ttu-id="baf8c-189">La sexta dirección IP posible del espacio de direcciones de la subred definida en el elemento 1 de la Tabla S.</span><span class="sxs-lookup"><span data-stu-id="baf8c-189">The sixth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |![línea](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="baf8c-191">4.</span><span class="sxs-lookup"><span data-stu-id="baf8c-191">4.</span></span>  <br/> |<span data-ttu-id="baf8c-192">Dirección IP estática del equilibrador de carga interno para los servidores de AD FS</span><span class="sxs-lookup"><span data-stu-id="baf8c-192">Static IP address of the internal load balancer for the AD FS servers</span></span>  <br/> |<span data-ttu-id="baf8c-193">La cuarta dirección IP posible del espacio de direcciones de la subred definida en el elemento 2 de la Tabla S.</span><span class="sxs-lookup"><span data-stu-id="baf8c-193">The fourth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |![línea](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="baf8c-195">5.</span><span class="sxs-lookup"><span data-stu-id="baf8c-195">5.</span></span>  <br/> |<span data-ttu-id="baf8c-196">Dirección IP estática del primer servidor de AD FS</span><span class="sxs-lookup"><span data-stu-id="baf8c-196">Static IP address of the first AD FS server</span></span>  <br/> |<span data-ttu-id="baf8c-197">La quinta dirección IP posible del espacio de direcciones de la subred definida en el elemento 2 de la Tabla S.</span><span class="sxs-lookup"><span data-stu-id="baf8c-197">The fifth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |![línea](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="baf8c-199">6.</span><span class="sxs-lookup"><span data-stu-id="baf8c-199">6.</span></span>  <br/> |<span data-ttu-id="baf8c-200">Dirección IP estática del segundo servidor de AD FS</span><span class="sxs-lookup"><span data-stu-id="baf8c-200">Static IP address of the second AD FS server</span></span>  <br/> |<span data-ttu-id="baf8c-201">La sexta dirección IP posible del espacio de direcciones de la subred definida en el elemento 2 de la Tabla S.</span><span class="sxs-lookup"><span data-stu-id="baf8c-201">The sixth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |![línea](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="baf8c-203">7.</span><span class="sxs-lookup"><span data-stu-id="baf8c-203">7.</span></span>  <br/> |<span data-ttu-id="baf8c-204">Dirección IP estática del primer servidor proxy de aplicación web</span><span class="sxs-lookup"><span data-stu-id="baf8c-204">Static IP address of the first web application proxy server</span></span>  <br/> |<span data-ttu-id="baf8c-205">La cuarta dirección IP posible del espacio de direcciones de la subred definida en el elemento 3 de la Tabla S.</span><span class="sxs-lookup"><span data-stu-id="baf8c-205">The fourth possible IP address for the address space of the subnet defined in Item 3 of Table S.</span></span>  <br/> |![línea](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="baf8c-207">8.</span><span class="sxs-lookup"><span data-stu-id="baf8c-207">8.</span></span>  <br/> |<span data-ttu-id="baf8c-208">Dirección IP estática del segundo servidor proxy de aplicación web</span><span class="sxs-lookup"><span data-stu-id="baf8c-208">Static IP address of the second web application proxy server</span></span>  <br/> |<span data-ttu-id="baf8c-209">La quinta dirección IP posible del espacio de direcciones de la subred definida en el elemento 3 de la Tabla S.</span><span class="sxs-lookup"><span data-stu-id="baf8c-209">The fifth possible IP address for the address space of the subnet defined in Item 3 of Table S.</span></span>  <br/> |![línea](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="baf8c-211">**Tabla I: Direcciones IP estáticas en la red virtual**</span><span class="sxs-lookup"><span data-stu-id="baf8c-211">**Table I: Static IP addresses in the virtual network**</span></span>
  
<span data-ttu-id="baf8c-212">Para dos servidores de Sistema de nombres de dominio (DNS) en la red local que quiera usar al configurar de manera inicial los controladores de dominio en la red virtual, rellene la Tabla D. Colabore con su departamento de TI para determinar esta lista.</span><span class="sxs-lookup"><span data-stu-id="baf8c-212">For two Domain Name System (DNS) servers in your on-premises network that you want to use when initially setting up the domain controllers in your virtual network, fill in Table D. Work with your IT department to determine this list.</span></span>
  
|<span data-ttu-id="baf8c-213">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="baf8c-213">**Item**</span></span>|<span data-ttu-id="baf8c-214">**Nombre descriptivo del servidor DNS**</span><span class="sxs-lookup"><span data-stu-id="baf8c-214">**DNS server friendly name**</span></span>|<span data-ttu-id="baf8c-215">**Dirección IP del servidor DNS**</span><span class="sxs-lookup"><span data-stu-id="baf8c-215">**DNS server IP address**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="baf8c-216">1.</span><span class="sxs-lookup"><span data-stu-id="baf8c-216">1.</span></span>  <br/> |![línea](./media/Common-Images/TableLine.png)  <br/> |![línea](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="baf8c-219">2.</span><span class="sxs-lookup"><span data-stu-id="baf8c-219">2.</span></span>  <br/> |![línea](./media/Common-Images/TableLine.png)  <br/> |![línea](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="baf8c-222">**Tabla D: Servidores DNS locales**</span><span class="sxs-lookup"><span data-stu-id="baf8c-222">**Table D: On-premises DNS servers**</span></span>
  
<span data-ttu-id="baf8c-223">Para enrutar paquetes desde la red entre locales a la red de la organización a través de la conexión VPN de sitio a sitio, debe configurar la red virtual con una red local que tenga una lista de espacios de direcciones (en notación CIDR) para todas las ubicaciones de acceso en la red local de su organización.</span><span class="sxs-lookup"><span data-stu-id="baf8c-223">To route packets from the cross-premises network to your organization network across the site-to-site VPN connection, you must configure the virtual network with a local network that has a list of the address spaces (in CIDR notation) for all of the reachable locations on your organization's on-premises network.</span></span> <span data-ttu-id="baf8c-224">La lista de espacios de direcciones que definen la red local tiene que ser única y no puede superponerse con el espacio de direcciones usado para otras redes virtuales ni otras redes locales.</span><span class="sxs-lookup"><span data-stu-id="baf8c-224">The list of address spaces that define your local network must be unique and must not overlap with the address space used for other virtual networks or other local networks.</span></span>
  
<span data-ttu-id="baf8c-225">For the set of local network address spaces, fill in Table L. Note that three blank entries are listed but you will typically need more.</span><span class="sxs-lookup"><span data-stu-id="baf8c-225">For the set of local network address spaces, fill in Table L. Note that three blank entries are listed but you will typically need more.</span></span> <span data-ttu-id="baf8c-226">Work with your IT department to determine this list of address spaces.</span><span class="sxs-lookup"><span data-stu-id="baf8c-226">Work with your IT department to determine this list of address spaces.</span></span>
  
|<span data-ttu-id="baf8c-227">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="baf8c-227">**Item**</span></span>|<span data-ttu-id="baf8c-228">**Espacio de direcciones de la red local**</span><span class="sxs-lookup"><span data-stu-id="baf8c-228">**Local network address space**</span></span>|
|:-----|:-----|
|<span data-ttu-id="baf8c-229">1.</span><span class="sxs-lookup"><span data-stu-id="baf8c-229">1.</span></span>  <br/> |![línea](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="baf8c-231">2.</span><span class="sxs-lookup"><span data-stu-id="baf8c-231">2.</span></span>  <br/> |![línea](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="baf8c-233">3.</span><span class="sxs-lookup"><span data-stu-id="baf8c-233">3.</span></span>  <br/> |![línea](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="baf8c-235">**Tabla L: Prefijos de direcciones para la red local**</span><span class="sxs-lookup"><span data-stu-id="baf8c-235">**Table L: Address prefixes for the local network**</span></span>
  
<span data-ttu-id="baf8c-236">Ahora, empecemos a crear la infraestructura de Azure para hospedar la autenticación federada para Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="baf8c-236">Now let's begin building the Azure infrastructure to host your federated authentication for Microsoft 365.</span></span>
  
> [!NOTE]
> <span data-ttu-id="baf8c-237">Los siguientes conjuntos de comandos utilizan la última versión de Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="baf8c-237">The following command sets use the latest version of Azure PowerShell.</span></span> <span data-ttu-id="baf8c-238">Consulte Introducción [a Azure PowerShell](https://docs.microsoft.com/powershell/azure/get-started-azureps).</span><span class="sxs-lookup"><span data-stu-id="baf8c-238">See [Get started with Azure PowerShell](https://docs.microsoft.com/powershell/azure/get-started-azureps).</span></span> 
  
<span data-ttu-id="baf8c-239">Primero, abra un símbolo del sistema de Azure PowerShell e inicie sesión con su cuenta.</span><span class="sxs-lookup"><span data-stu-id="baf8c-239">First, start an Azure PowerShell prompt and login to your account.</span></span>
  
```powershell
Connect-AzAccount
```

> [!TIP]
> <span data-ttu-id="baf8c-240">Para generar bloques de comandos de PowerShell listos para ejecutar en función de la configuración personalizada, use este [libro de configuración de Microsoft Excel](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx).</span><span class="sxs-lookup"><span data-stu-id="baf8c-240">To generate ready-to-run PowerShell command blocks based on your custom settings, use this [Microsoft Excel configuration workbook](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx).</span></span> 

<span data-ttu-id="baf8c-241">Obtenga su nombre de suscripción mediante el comando siguiente.</span><span class="sxs-lookup"><span data-stu-id="baf8c-241">Get your subscription name using the following command.</span></span>
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

<span data-ttu-id="baf8c-242">Para las versiones anteriores de Azure PowerShell, use este comando en su lugar.</span><span class="sxs-lookup"><span data-stu-id="baf8c-242">For older versions of Azure PowerShell, use this command instead.</span></span>
  
```powershell
Get-AzSubscription | Sort Name | Select SubscriptionName
```

<span data-ttu-id="baf8c-243">Configure su suscripción de Azure.</span><span class="sxs-lookup"><span data-stu-id="baf8c-243">Set your Azure subscription.</span></span> <span data-ttu-id="baf8c-244">Reemplace todo lo que haya entre las comillas, incluidos los \< and > caracteres, por el nombre correcto.</span><span class="sxs-lookup"><span data-stu-id="baf8c-244">Replace everything within the quotes, including the \< and > characters, with the correct name.</span></span>
  
```powershell
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

<span data-ttu-id="baf8c-245">Next, create the new resource groups.</span><span class="sxs-lookup"><span data-stu-id="baf8c-245">Next, create the new resource groups.</span></span> <span data-ttu-id="baf8c-246">To determine a unique set of resource group names, use this command to list your existing resource groups.</span><span class="sxs-lookup"><span data-stu-id="baf8c-246">To determine a unique set of resource group names, use this command to list your existing resource groups.</span></span>
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="baf8c-247">Rellene la tabla siguiente para el conjunto de nombres de grupos de recursos únicos.</span><span class="sxs-lookup"><span data-stu-id="baf8c-247">Fill in the following table for the set of unique resource group names.</span></span>
  
|<span data-ttu-id="baf8c-248">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="baf8c-248">**Item**</span></span>|<span data-ttu-id="baf8c-249">**Nombre del grupo de recursos**</span><span class="sxs-lookup"><span data-stu-id="baf8c-249">**Resource group name**</span></span>|<span data-ttu-id="baf8c-250">**Finalidad**</span><span class="sxs-lookup"><span data-stu-id="baf8c-250">**Purpose**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="baf8c-251">1.</span><span class="sxs-lookup"><span data-stu-id="baf8c-251">1.</span></span>  <br/> |![línea](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="baf8c-253">Controladores de dominio</span><span class="sxs-lookup"><span data-stu-id="baf8c-253">Domain controllers</span></span>  <br/> |
|<span data-ttu-id="baf8c-254">2.</span><span class="sxs-lookup"><span data-stu-id="baf8c-254">2.</span></span>  <br/> |![línea](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="baf8c-256">Servidores de AD FS</span><span class="sxs-lookup"><span data-stu-id="baf8c-256">AD FS servers</span></span>  <br/> |
|<span data-ttu-id="baf8c-257">3.</span><span class="sxs-lookup"><span data-stu-id="baf8c-257">3.</span></span>  <br/> |![línea](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="baf8c-259">Servidores proxy de aplicación web</span><span class="sxs-lookup"><span data-stu-id="baf8c-259">Web application proxy servers</span></span>  <br/> |
|<span data-ttu-id="baf8c-260">4.</span><span class="sxs-lookup"><span data-stu-id="baf8c-260">4.</span></span>  <br/> |![línea](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="baf8c-262">Elementos de la infraestructura</span><span class="sxs-lookup"><span data-stu-id="baf8c-262">Infrastructure elements</span></span>  <br/> |
   
 <span data-ttu-id="baf8c-263">**Tabla R: Grupos de recursos**</span><span class="sxs-lookup"><span data-stu-id="baf8c-263">**Table R: Resource groups**</span></span>
  
<span data-ttu-id="baf8c-264">Cree el grupo de recursos con estos comandos.</span><span class="sxs-lookup"><span data-stu-id="baf8c-264">Create your new resource groups with these commands.</span></span>
  
```powershell
$locName="<an Azure location, such as West US>"
$rgName="<Table R - Item 1 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 2 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 3 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 4 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="baf8c-265">Después, cree la red virtual de Azure y sus subredes.</span><span class="sxs-lookup"><span data-stu-id="baf8c-265">Next, you create the Azure virtual network and its subnets.</span></span>
  
```powershell
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnetAddrPrefix="<Table V - Item 4 - Value column>"
$dnsServers=@( "<Table D - Item 1 - DNS server IP address column>", "<Table D - Item 2 - DNS server IP address column>" )
# Get the shortened version of the location
$locShortName=(Get-AzResourceGroup -Name $rgName).Location

# Create the subnets
$subnet1Name="<Table S - Item 1 - Subnet name column>"
$subnet1Prefix="<Table S - Item 1 - Subnet address space column>"
$subnet1=New-AzVirtualNetworkSubnetConfig -Name $subnet1Name -AddressPrefix $subnet1Prefix
$subnet2Name="<Table S - Item 2 - Subnet name column>"
$subnet2Prefix="<Table S - Item 2 - Subnet address space column>"
$subnet2=New-AzVirtualNetworkSubnetConfig -Name $subnet2Name -AddressPrefix $subnet2Prefix
$subnet3Name="<Table S - Item 3 - Subnet name column>"
$subnet3Prefix="<Table S - Item 3 - Subnet address space column>"
$subnet3=New-AzVirtualNetworkSubnetConfig -Name $subnet3Name -AddressPrefix $subnet3Prefix
$gwSubnet4Prefix="<Table S - Item 4 - Subnet address space column>"
$gwSubnet=New-AzVirtualNetworkSubnetConfig -Name "GatewaySubnet" -AddressPrefix $gwSubnet4Prefix

# Create the virtual network
New-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName -Location $locName -AddressPrefix $vnetAddrPrefix -Subnet $gwSubnet,$subnet1,$subnet2,$subnet3 -DNSServer $dnsServers

```

<span data-ttu-id="baf8c-266">A continuación, cree grupos de seguridad de red para cada subred que tenga máquinas virtuales.</span><span class="sxs-lookup"><span data-stu-id="baf8c-266">Next, you create network security groups for each subnet that has virtual machines.</span></span> <span data-ttu-id="baf8c-267">Para realizar el aislamiento de la subred, puede agregar reglas para tipos específicos de tráfico permitido o denegado para el grupo de seguridad de red de una subred.</span><span class="sxs-lookup"><span data-stu-id="baf8c-267">To perform subnet isolation, you can add rules for the specific types of traffic allowed or denied to the network security group of a subnet.</span></span>
  
```powershell
# Create network security groups
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name $vnetName

New-AzNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet1Name -AddressPrefix $subnet1Prefix -NetworkSecurityGroup $nsg

New-AzNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet2Name -AddressPrefix $subnet2Prefix -NetworkSecurityGroup $nsg

New-AzNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet3Name -AddressPrefix $subnet3Prefix -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
```

<span data-ttu-id="baf8c-268">Después, use estos comandos para crear las puertas de enlace para la conexión VPN de sitio a sitio.</span><span class="sxs-lookup"><span data-stu-id="baf8c-268">Next, use these commands to create the gateways for the site-to-site VPN connection.</span></span>
  
```powershell
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "GatewaySubnet"

# Attach a virtual network gateway to a public IP address and the gateway subnet
$publicGatewayVipName="PublicIPAddress"
$vnetGatewayIpConfigName="PublicIPConfig"
New-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$publicGatewayVip=Get-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName
$vnetGatewayIpConfig=New-AzVirtualNetworkGatewayIpConfig -Name $vnetGatewayIpConfigName -PublicIpAddressId $publicGatewayVip.Id -Subnet $subnet

# Create the Azure gateway
$vnetGatewayName="AzureGateway"
$vnetGateway=New-AzVirtualNetworkGateway -Name $vnetGatewayName -ResourceGroupName $rgName -Location $locName -GatewayType Vpn -VpnType RouteBased -IpConfigurations $vnetGatewayIpConfig

# Create the gateway for the local network
$localGatewayName="LocalNetGateway"
$localGatewayIP="<Table V - Item 3 - Value column>"
$localNetworkPrefix=@( <comma-separated, double-quote enclosed list of the local network address prefixes from Table L, example: "10.1.0.0/24", "10.2.0.0/24"> )
$localGateway=New-AzLocalNetworkGateway -Name $localGatewayName -ResourceGroupName $rgName -Location $locName -GatewayIpAddress $localGatewayIP -AddressPrefix $localNetworkPrefix

# Define the Azure virtual network VPN connection
$vnetConnectionName="S2SConnection"
$vnetConnectionKey="<Table V - Item 5 - Value column>"
$vnetConnection=New-AzVirtualNetworkGatewayConnection -Name $vnetConnectionName -ResourceGroupName $rgName -Location $locName -ConnectionType IPsec -SharedKey $vnetConnectionKey -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localGateway

```

> [!NOTE]
> <span data-ttu-id="baf8c-269">La autenticación federada de los usuarios individuales no se basa en los recursos locales.</span><span class="sxs-lookup"><span data-stu-id="baf8c-269">Federated authentication of individual users does not rely on any on-premises resources.</span></span> <span data-ttu-id="baf8c-270">Sin embargo, si esta conexión VPN de sitio a sitio deja de estar disponible, los controladores de dominio de la red virtual no recibirán actualizaciones de las cuentas de usuario y los grupos realizados en los servicios de dominio de Active Directory local.</span><span class="sxs-lookup"><span data-stu-id="baf8c-270">However, if this site-to-site VPN connection becomes unavailable, the domain controllers in the VNet will not receive updates to user accounts and groups made in the on-premises Active Directory Domain Services.</span></span> <span data-ttu-id="baf8c-271">Para asegurarse de que esto no suceda, puede configurar la alta disponibilidad para la conexión VPN de sitio a sitio.</span><span class="sxs-lookup"><span data-stu-id="baf8c-271">To ensure this does not happen, you can configure high availability for your site-to-site VPN connection.</span></span> <span data-ttu-id="baf8c-272">Para obtener más información, consulte [Conectividad de red virtual a red virtual y con alta disponibilidad entre locales](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span><span class="sxs-lookup"><span data-stu-id="baf8c-272">For more information, see [Highly Available Cross-Premises and VNet-to-VNet Connectivity](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span></span>
  
<span data-ttu-id="baf8c-273">El paso siguiente es anotar la dirección IPv4 pública de Azure VPN Gateway para la red virtual después de ejecutar este comando:</span><span class="sxs-lookup"><span data-stu-id="baf8c-273">Next, record the public IPv4 address of the Azure VPN gateway for your virtual network from the display of this command:</span></span>
  
```powershell
Get-AzPublicIpAddress -Name $publicGatewayVipName -ResourceGroupName $rgName
```

<span data-ttu-id="baf8c-274">Next, configure your on-premises VPN device to connect to the Azure VPN gateway.</span><span class="sxs-lookup"><span data-stu-id="baf8c-274">Next, configure your on-premises VPN device to connect to the Azure VPN gateway.</span></span> <span data-ttu-id="baf8c-275">For more information, see [Configure your VPN device](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span><span class="sxs-lookup"><span data-stu-id="baf8c-275">For more information, see [Configure your VPN device](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="baf8c-276">Para configurar el dispositivo VPN local necesita lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="baf8c-276">To configure your on-premises VPN device, you will need the following:</span></span>
  
- <span data-ttu-id="baf8c-277">La dirección IPv4 pública de Azure VPN Gateway.</span><span class="sxs-lookup"><span data-stu-id="baf8c-277">The public IPv4 address of the Azure VPN gateway.</span></span>
    
- <span data-ttu-id="baf8c-278">La clave precompartida IPsec para la conexión VPN de sitio a sitio (Tabla V, elemento 5, columna Valor).</span><span class="sxs-lookup"><span data-stu-id="baf8c-278">The IPsec pre-shared key for the site-to-site VPN connection (Table V - Item 5 - Value column).</span></span>
    
<span data-ttu-id="baf8c-279">Next, ensure that the address space of the virtual network is reachable from your on-premises network.</span><span class="sxs-lookup"><span data-stu-id="baf8c-279">Next, ensure that the address space of the virtual network is reachable from your on-premises network.</span></span> <span data-ttu-id="baf8c-280">This is usually done by adding a route corresponding to the virtual network address space to your VPN device and then advertising that route to the rest of the routing infrastructure of your organization network.</span><span class="sxs-lookup"><span data-stu-id="baf8c-280">This is usually done by adding a route corresponding to the virtual network address space to your VPN device and then advertising that route to the rest of the routing infrastructure of your organization network.</span></span> <span data-ttu-id="baf8c-281">Work with your IT department to determine how to do this.</span><span class="sxs-lookup"><span data-stu-id="baf8c-281">Work with your IT department to determine how to do this.</span></span>
  
<span data-ttu-id="baf8c-282">Next, define the names of three availability sets.</span><span class="sxs-lookup"><span data-stu-id="baf8c-282">Next, define the names of three availability sets.</span></span> <span data-ttu-id="baf8c-283">Fill out Table A.</span><span class="sxs-lookup"><span data-stu-id="baf8c-283">Fill out Table A.</span></span> 
  
|<span data-ttu-id="baf8c-284">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="baf8c-284">**Item**</span></span>|<span data-ttu-id="baf8c-285">**Objetivo**</span><span class="sxs-lookup"><span data-stu-id="baf8c-285">**Purpose**</span></span>|<span data-ttu-id="baf8c-286">**Nombre del conjunto de disponibilidad**</span><span class="sxs-lookup"><span data-stu-id="baf8c-286">**Availability set name**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="baf8c-287">1.</span><span class="sxs-lookup"><span data-stu-id="baf8c-287">1.</span></span>  <br/> |<span data-ttu-id="baf8c-288">Controladores de dominio</span><span class="sxs-lookup"><span data-stu-id="baf8c-288">Domain controllers</span></span>  <br/> |![línea](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="baf8c-290">2.</span><span class="sxs-lookup"><span data-stu-id="baf8c-290">2.</span></span>  <br/> |<span data-ttu-id="baf8c-291">Servidores de AD FS</span><span class="sxs-lookup"><span data-stu-id="baf8c-291">AD FS servers</span></span>  <br/> |![línea](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="baf8c-293">3.</span><span class="sxs-lookup"><span data-stu-id="baf8c-293">3.</span></span>  <br/> |<span data-ttu-id="baf8c-294">Servidores proxy de aplicación web</span><span class="sxs-lookup"><span data-stu-id="baf8c-294">Web application proxy servers</span></span>  <br/> |![línea](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="baf8c-296">**Tabla A: Conjuntos de disponibilidad**</span><span class="sxs-lookup"><span data-stu-id="baf8c-296">**Table A: Availability sets**</span></span>
  
<span data-ttu-id="baf8c-297">Necesitará estos nombres al crear las máquinas virtuales en las fases 2, 3 y 4.</span><span class="sxs-lookup"><span data-stu-id="baf8c-297">You will need these names when you create the virtual machines in phases 2, 3, and 4.</span></span>
  
<span data-ttu-id="baf8c-298">Cree los conjuntos de disponibilidad con estos comandos de Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="baf8c-298">Create the new availability sets with these Azure PowerShell commands.</span></span>
  
```powershell
$locName="<the Azure location for your new resource group>"
$rgName="<Table R - Item 1 - Resource group name column>"
$avName="<Table A - Item 1 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
$rgName="<Table R - Item 2 - Resource group name column>"
$avName="<Table A - Item 2 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
$rgName="<Table R - Item 3 - Resource group name column>"
$avName="<Table A - Item 3 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
```

<span data-ttu-id="baf8c-299">Esta es la configuración que se muestra después de la finalización correcta de esta fase.</span><span class="sxs-lookup"><span data-stu-id="baf8c-299">This is the configuration resulting from the successful completion of this phase.</span></span>
  
<span data-ttu-id="baf8c-300">**Fase 1: la infraestructura de Azure para la autenticación federada de alta disponibilidad para Microsoft 365**</span><span class="sxs-lookup"><span data-stu-id="baf8c-300">**Phase 1: The Azure infrastructure for high availability federated authentication for Microsoft 365**</span></span>

![Fase 1 de la autenticación federada de alta disponibilidad Microsoft 365 en Azure con la infraestructura de Azure](media/4e7ba678-07df-40ce-b372-021bf7fc91fa.png)
  
## <a name="next-step"></a><span data-ttu-id="baf8c-302">Paso siguiente</span><span class="sxs-lookup"><span data-stu-id="baf8c-302">Next step</span></span>

<span data-ttu-id="baf8c-303">Use [Phase 2: configure Domain Controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) para continuar con la configuración de esta carga de trabajo.</span><span class="sxs-lookup"><span data-stu-id="baf8c-303">Use [Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) to continue with the configuration of this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="baf8c-304">Vea también</span><span class="sxs-lookup"><span data-stu-id="baf8c-304">See Also</span></span>

[<span data-ttu-id="baf8c-305">Implementar la autenticación federada de alta disponibilidad para Microsoft 365 en Azure</span><span class="sxs-lookup"><span data-stu-id="baf8c-305">Deploy high availability federated authentication for Microsoft 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="baf8c-306">Identidad federada para el entorno de prueba y desarrollo de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="baf8c-306">Federated identity for your Microsoft 365 dev/test environment</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/federated-identity-for-your-office-365-dev-test-environment)
  
[<span data-ttu-id="baf8c-307">Adopción de la nube y soluciones híbridas</span><span class="sxs-lookup"><span data-stu-id="baf8c-307">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.yml)

[<span data-ttu-id="baf8c-308">Descripción de la identidad de Microsoft 365 y Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="baf8c-308">Understanding Microsoft 365 identity and Azure Active Directory</span></span>](about-office-365-identity.md)


