---
title: Fase 1 de la autenticación federada de alta disponibilidad configurar Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/15/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 91266aac-4d00-4b5f-b424-86a1a837792c
description: 'Resumen: Configure la infraestructura de Microsoft Azure para que hospede la autenticación federada de alta disponibilidad para Office 365.'
ms.openlocfilehash: 0268178b12374f200181c0f1b8a38de6a39e7173
ms.sourcegitcommit: dffbcfb1cbc9776a29229a787c1eab4192e55cff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/28/2019
ms.locfileid: "30948611"
---
# <a name="high-availability-federated-authentication-phase-1-configure-azure"></a><span data-ttu-id="2b00b-103">Fase 1 de la autenticación federada de alta disponibilidad: Configurar Azure</span><span class="sxs-lookup"><span data-stu-id="2b00b-103">High availability federated authentication Phase 1: Configure Azure</span></span>

 <span data-ttu-id="2b00b-104">**Resumen:** Configure la infraestructura de Microsoft Azure para que hospede la autenticación federada de alta disponibilidad para Office 365.</span><span class="sxs-lookup"><span data-stu-id="2b00b-104">**Summary:** Configure the Microsoft Azure infrastructure to host high availability federated authentication for Office 365.</span></span>
  
<span data-ttu-id="2b00b-105">En esta fase, se crean los grupos de recursos, la red virtual (VNet) y los conjuntos de disponibilidad en Azure que hospedarán las máquinas virtuales en las fases 2, 3 y 4.</span><span class="sxs-lookup"><span data-stu-id="2b00b-105">In this phase, you create the resource groups, virtual network (VNet), and availability sets in Azure that will host the virtual machines in phases 2, 3, and 4.</span></span> <span data-ttu-id="2b00b-106">Debe completar esta fase antes de pasar a la [fase 2 de la autenticación federada de alta disponibilidad: configurar controladores de dominio](high-availability-federated-authentication-phase-2-configure-domain-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="2b00b-106">You must complete this phase before moving on to [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md).</span></span> <span data-ttu-id="2b00b-107">Consulte todas las fases en [Implementar la autenticación federada de alta disponibilidad para Office 365 en Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).</span><span class="sxs-lookup"><span data-stu-id="2b00b-107">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
<span data-ttu-id="2b00b-108">Azure debe estar aprovisionado con estos componentes básicos:</span><span class="sxs-lookup"><span data-stu-id="2b00b-108">Azure must be provisioned with these basic components:</span></span>
  
- <span data-ttu-id="2b00b-109">Grupos de recursos</span><span class="sxs-lookup"><span data-stu-id="2b00b-109">Resource groups</span></span>
    
- <span data-ttu-id="2b00b-110">Una red virtual (VNET) de Azure entre locales con subredes para hospedar las máquinas virtuales de Azure</span><span class="sxs-lookup"><span data-stu-id="2b00b-110">A cross-premises Azure virtual network (VNet) with subnets for hosting the Azure virtual machines</span></span>
    
- <span data-ttu-id="2b00b-111">Grupos de seguridad de red para realizar el aislamiento de subredes</span><span class="sxs-lookup"><span data-stu-id="2b00b-111">Network security groups for performing subnet isolation</span></span>
    
- <span data-ttu-id="2b00b-112">Conjuntos de disponibilidad</span><span class="sxs-lookup"><span data-stu-id="2b00b-112">Availability sets</span></span>
    
## <a name="configure-azure-components"></a><span data-ttu-id="2b00b-113">Configurar componentes de Azure</span><span class="sxs-lookup"><span data-stu-id="2b00b-113">Configure Azure components</span></span>

<span data-ttu-id="2b00b-114">Antes de empezar a configurar los componentes de Azure, rellene las tablas siguientes.</span><span class="sxs-lookup"><span data-stu-id="2b00b-114">Before you begin configuring Azure components, fill in the following tables.</span></span> <span data-ttu-id="2b00b-115">Para ayudarle en los procedimientos de configuración de Azure, imprima esta sección y anote la información necesaria, o bien copie esta sección en un documento y rellénelo.</span><span class="sxs-lookup"><span data-stu-id="2b00b-115">To assist you in the procedures for configuring Azure, print this section and write down the needed information or copy this section to a document and fill it in.</span></span> <span data-ttu-id="2b00b-116">Para la configuración de la red virtual, rellene la tabla V.</span><span class="sxs-lookup"><span data-stu-id="2b00b-116">For the settings of the VNet, fill in Table V.</span></span>
  
|<span data-ttu-id="2b00b-117">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="2b00b-117">**Item**</span></span>|<span data-ttu-id="2b00b-118">**Opción de configuración**</span><span class="sxs-lookup"><span data-stu-id="2b00b-118">**Configuration setting**</span></span>|<span data-ttu-id="2b00b-119">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="2b00b-119">**Description**</span></span>|<span data-ttu-id="2b00b-120">**Valor**</span><span class="sxs-lookup"><span data-stu-id="2b00b-120">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="2b00b-121">1.</span><span class="sxs-lookup"><span data-stu-id="2b00b-121">1.</span></span>  <br/> |<span data-ttu-id="2b00b-122">Nombre de VNET</span><span class="sxs-lookup"><span data-stu-id="2b00b-122">VNet name</span></span>  <br/> |<span data-ttu-id="2b00b-123">Nombre que se asignará a la red virtual (por ejemplo, FedAuthNet).</span><span class="sxs-lookup"><span data-stu-id="2b00b-123">A name to assign to the VNet (example FedAuthNet).</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="2b00b-124">2.</span><span class="sxs-lookup"><span data-stu-id="2b00b-124">2.</span></span>  <br/> |<span data-ttu-id="2b00b-125">Ubicación de la VNET</span><span class="sxs-lookup"><span data-stu-id="2b00b-125">VNet location</span></span>  <br/> |<span data-ttu-id="2b00b-126">Centro de datos regional de Azure que contendrá la red virtual.</span><span class="sxs-lookup"><span data-stu-id="2b00b-126">The regional Azure datacenter that will contain the virtual network.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="2b00b-127">3.</span><span class="sxs-lookup"><span data-stu-id="2b00b-127">3.</span></span>  <br/> |<span data-ttu-id="2b00b-128">Dirección IP del dispositivo VPN</span><span class="sxs-lookup"><span data-stu-id="2b00b-128">VPN device IP address</span></span>  <br/> |<span data-ttu-id="2b00b-129">Dirección IPv4 pública de la interfaz del dispositivo VPN en Internet.</span><span class="sxs-lookup"><span data-stu-id="2b00b-129">The public IPv4 address of your VPN device's interface on the Internet.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="2b00b-130">4.</span><span class="sxs-lookup"><span data-stu-id="2b00b-130">4.</span></span>  <br/> |<span data-ttu-id="2b00b-131">Espacio de direcciones de la VNET</span><span class="sxs-lookup"><span data-stu-id="2b00b-131">VNet address space</span></span>  <br/> |<span data-ttu-id="2b00b-p103">El espacio de direcciones de la red virtual. Colabore con su departamento de TI para determinar este espacio de direcciones.</span><span class="sxs-lookup"><span data-stu-id="2b00b-p103">The address space for the virtual network. Work with your IT department to determine this address space.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="2b00b-134">5.</span><span class="sxs-lookup"><span data-stu-id="2b00b-134">5.</span></span>  <br/> |<span data-ttu-id="2b00b-135">Clave compartida IPsec</span><span class="sxs-lookup"><span data-stu-id="2b00b-135">IPsec shared key</span></span>  <br/> |<span data-ttu-id="2b00b-p104">Cadena alfanumérica aleatoria de 32 caracteres que se usará para autenticar ambos lados de la conexión VPN de sitio a sitio. Colabore con su departamento de TI o de seguridad para determinar el valor de la clave y, después, guárdelo en una ubicación segura. También puede ver [Crear una cadena aleatoria para una clave precompartida IPsec](http://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  </span><span class="sxs-lookup"><span data-stu-id="2b00b-p104">A 32-character random, alphanumeric string that will be used to authenticate both sides of the site-to-site VPN connection. Work with your IT or security department to determine this key value. Alternately, see [Create a random string for an IPsec preshared key](http://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  </span></span><br/> |![](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="2b00b-139">**Tabla V: Configuración de la red virtual entre locales**</span><span class="sxs-lookup"><span data-stu-id="2b00b-139">**Table V: Cross-premises virtual network configuration**</span></span>
  
<span data-ttu-id="2b00b-p105">Después, rellene la Tabla S de las subredes de esta solución. Todos los espacios de direcciones tienen que estar en formato de Enrutamiento de interdominios sin clases (CIDR), también conocido como formato de prefijo de red (por ejemplo, 10.24.64.0/20).</span><span class="sxs-lookup"><span data-stu-id="2b00b-p105">Next, fill in Table S for the subnets of this solution. All address spaces should be in Classless Interdomain Routing (CIDR) format, also known as network prefix format. An example is 10.24.64.0/20.</span></span>
  
<span data-ttu-id="2b00b-p106">Para las primeras tres subredes, especifique un nombre y un espacio de direcciones IP único basándose en el espacio de direcciones de la red virtual. Para la subred de la puerta de enlace, determine el espacio de direcciones de 27 bits (con una longitud de prefijo de /27) para la subred de puerta de enlace de Azure con lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="2b00b-p106">For the first three subnets, specify a name and a single IP address space based on the virtual network address space. For the gateway subnet, determine the 27-bit address space (with a /27 prefix length) for the Azure gateway subnet with the following:</span></span>
  
1. <span data-ttu-id="2b00b-145">Establezca los bits variables en el espacio de direcciones de la VNET en 1, hasta los bits usados por la subred de la puerta de enlace y, después, establezca el resto de los bits en 0.</span><span class="sxs-lookup"><span data-stu-id="2b00b-145">Set the variable bits in the address space of the VNet to 1, up to the bits being used by the gateway subnet, then set the remaining bits to 0.</span></span>
    
2. <span data-ttu-id="2b00b-146">Convierta los bits resultantes a decimales y expréselo como un espacio de direcciones con la longitud de prefijo establecida en el tamaño de la subred de puerta de enlace.</span><span class="sxs-lookup"><span data-stu-id="2b00b-146">Convert the resulting bits to decimal and express it as an address space with the prefix length set to the size of the gateway subnet.</span></span>
    
<span data-ttu-id="2b00b-147">Vea [calculadora de espacio de direcciones para subredes de puerta de enlace de Azure](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) para obtener un bloque de comandos de PowerShell y una aplicación de consola de C# o Python que realice este cálculo.</span><span class="sxs-lookup"><span data-stu-id="2b00b-147">See [Address space calculator for Azure gateway subnets](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) for a PowerShell command block and C# or Python console application that performs this calculation for you.</span></span>
  
<span data-ttu-id="2b00b-148">Trabaje con su departamento de TI para determinar estos espacios de direcciones a partir del espacio de direcciones de la red virtual.</span><span class="sxs-lookup"><span data-stu-id="2b00b-148">Work with your IT department to determine these address spaces from the virtual network address space.</span></span>
  
|<span data-ttu-id="2b00b-149">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="2b00b-149">**Item**</span></span>|<span data-ttu-id="2b00b-150">**Nombre de la subred**</span><span class="sxs-lookup"><span data-stu-id="2b00b-150">**Subnet name**</span></span>|<span data-ttu-id="2b00b-151">**Espacio de direcciones de la subred**</span><span class="sxs-lookup"><span data-stu-id="2b00b-151">**Subnet address space**</span></span>|<span data-ttu-id="2b00b-152">**Finalidad**</span><span class="sxs-lookup"><span data-stu-id="2b00b-152">**Purpose**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="2b00b-153">1.</span><span class="sxs-lookup"><span data-stu-id="2b00b-153">1.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="2b00b-154">La subred que usa el controlador de dominio de Windows Server Active Directory (AD) y las máquinas virtuales (VM) del servidor de DirSync.</span><span class="sxs-lookup"><span data-stu-id="2b00b-154">The subnet used by the Windows Server Active Directory (AD) domain controller and DirSync server virtual machines (VMs).</span></span>  <br/> |
|<span data-ttu-id="2b00b-155">2.</span><span class="sxs-lookup"><span data-stu-id="2b00b-155">2.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="2b00b-156">Subred usada por las máquinas virtuales de AD FS.</span><span class="sxs-lookup"><span data-stu-id="2b00b-156">The subnet used by the AD FS VMs.</span></span>  <br/> |
|<span data-ttu-id="2b00b-157">3.</span><span class="sxs-lookup"><span data-stu-id="2b00b-157">3.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="2b00b-158">Subred usada por las máquinas virtuales del proxy de aplicación web.</span><span class="sxs-lookup"><span data-stu-id="2b00b-158">The subnet used by the web application proxy VMs.</span></span>  <br/> |
|<span data-ttu-id="2b00b-159">4.</span><span class="sxs-lookup"><span data-stu-id="2b00b-159">4.</span></span>  <br/> |<span data-ttu-id="2b00b-160">GatewaySubnet</span><span class="sxs-lookup"><span data-stu-id="2b00b-160">GatewaySubnet</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="2b00b-161">Subred usada por las máquinas virtuales de la puerta de enlace de Azure.</span><span class="sxs-lookup"><span data-stu-id="2b00b-161">The subnet used by the Azure gateway VMs.</span></span>  <br/> |
   
 <span data-ttu-id="2b00b-162">**Tabla S: Subredes de la red virtual**</span><span class="sxs-lookup"><span data-stu-id="2b00b-162">**Table S: Subnets in the virtual network**</span></span>
  
<span data-ttu-id="2b00b-163">Ahora, rellene la Tabla I para las direcciones IP estáticas asignadas a las máquinas virtuales y a las instancias del equilibrador de carga.</span><span class="sxs-lookup"><span data-stu-id="2b00b-163">Next, fill in Table I for the static IP addresses assigned to virtual machines and load balancer instances.</span></span>
  
|<span data-ttu-id="2b00b-164">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="2b00b-164">**Item**</span></span>|<span data-ttu-id="2b00b-165">**Objetivo**</span><span class="sxs-lookup"><span data-stu-id="2b00b-165">**Purpose**</span></span>|<span data-ttu-id="2b00b-166">**Dirección IP en la subred**</span><span class="sxs-lookup"><span data-stu-id="2b00b-166">**IP address on the subnet**</span></span>|<span data-ttu-id="2b00b-167">**Valor**</span><span class="sxs-lookup"><span data-stu-id="2b00b-167">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="2b00b-168">1.</span><span class="sxs-lookup"><span data-stu-id="2b00b-168">1.</span></span>  <br/> |<span data-ttu-id="2b00b-169">Dirección IP estática del primer controlador de dominio</span><span class="sxs-lookup"><span data-stu-id="2b00b-169">Static IP address of the first domain controller</span></span>  <br/> |<span data-ttu-id="2b00b-170">La cuarta dirección IP posible del espacio de direcciones de la subred definida en el elemento 1 de la Tabla S.</span><span class="sxs-lookup"><span data-stu-id="2b00b-170">The fourth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="2b00b-171">2.</span><span class="sxs-lookup"><span data-stu-id="2b00b-171">2.</span></span>  <br/> |<span data-ttu-id="2b00b-172">Dirección IP estática del segundo controlador de dominio</span><span class="sxs-lookup"><span data-stu-id="2b00b-172">Static IP address of the second domain controller</span></span>  <br/> |<span data-ttu-id="2b00b-173">La quinta dirección IP posible del espacio de direcciones de la subred definida en el elemento 1 de la Tabla S.</span><span class="sxs-lookup"><span data-stu-id="2b00b-173">The fifth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="2b00b-174">3.</span><span class="sxs-lookup"><span data-stu-id="2b00b-174">3.</span></span>  <br/> |<span data-ttu-id="2b00b-175">Dirección IP estática del servidor de DirSync</span><span class="sxs-lookup"><span data-stu-id="2b00b-175">Static IP address of the DirSync server</span></span>  <br/> |<span data-ttu-id="2b00b-176">La sexta dirección IP posible del espacio de direcciones de la subred definida en el elemento 1 de la Tabla S.</span><span class="sxs-lookup"><span data-stu-id="2b00b-176">The sixth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="2b00b-177">4.</span><span class="sxs-lookup"><span data-stu-id="2b00b-177">4.</span></span>  <br/> |<span data-ttu-id="2b00b-178">Dirección IP estática del equilibrador de carga interno para los servidores de AD FS</span><span class="sxs-lookup"><span data-stu-id="2b00b-178">Static IP address of the internal load balancer for the AD FS servers</span></span>  <br/> |<span data-ttu-id="2b00b-179">La cuarta dirección IP posible del espacio de direcciones de la subred definida en el elemento 2 de la Tabla S.</span><span class="sxs-lookup"><span data-stu-id="2b00b-179">The fourth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="2b00b-180">5.</span><span class="sxs-lookup"><span data-stu-id="2b00b-180">5.</span></span>  <br/> |<span data-ttu-id="2b00b-181">Dirección IP estática del primer servidor de AD FS</span><span class="sxs-lookup"><span data-stu-id="2b00b-181">Static IP address of the first AD FS server</span></span>  <br/> |<span data-ttu-id="2b00b-182">La quinta dirección IP posible del espacio de direcciones de la subred definida en el elemento 2 de la Tabla S.</span><span class="sxs-lookup"><span data-stu-id="2b00b-182">The fifth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="2b00b-183">6.</span><span class="sxs-lookup"><span data-stu-id="2b00b-183">6.</span></span>  <br/> |<span data-ttu-id="2b00b-184">Dirección IP estática del segundo servidor de AD FS</span><span class="sxs-lookup"><span data-stu-id="2b00b-184">Static IP address of the second AD FS server</span></span>  <br/> |<span data-ttu-id="2b00b-185">La sexta dirección IP posible del espacio de direcciones de la subred definida en el elemento 2 de la Tabla S.</span><span class="sxs-lookup"><span data-stu-id="2b00b-185">The sixth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="2b00b-186">7.</span><span class="sxs-lookup"><span data-stu-id="2b00b-186">7.</span></span>  <br/> |<span data-ttu-id="2b00b-187">Dirección IP estática del primer servidor proxy de aplicación web</span><span class="sxs-lookup"><span data-stu-id="2b00b-187">Static IP address of the first web application proxy server</span></span>  <br/> |<span data-ttu-id="2b00b-188">La cuarta dirección IP posible del espacio de direcciones de la subred definida en el elemento 3 de la Tabla S.</span><span class="sxs-lookup"><span data-stu-id="2b00b-188">The fourth possible IP address for the address space of the subnet defined in Item 3 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="2b00b-189">8.</span><span class="sxs-lookup"><span data-stu-id="2b00b-189">8.</span></span>  <br/> |<span data-ttu-id="2b00b-190">Dirección IP estática del segundo servidor proxy de aplicación web</span><span class="sxs-lookup"><span data-stu-id="2b00b-190">Static IP address of the second web application proxy server</span></span>  <br/> |<span data-ttu-id="2b00b-191">La quinta dirección IP posible del espacio de direcciones de la subred definida en el elemento 3 de la Tabla S.</span><span class="sxs-lookup"><span data-stu-id="2b00b-191">The fifth possible IP address for the address space of the subnet defined in Item 3 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="2b00b-192">**Tabla I: Direcciones IP estáticas en la red virtual**</span><span class="sxs-lookup"><span data-stu-id="2b00b-192">**Table I: Static IP addresses in the virtual network**</span></span>
  
<span data-ttu-id="2b00b-193">Para dos servidores de Sistema de nombres de dominio (DNS) en la red local que quiera usar al configurar de manera inicial los controladores de dominio en la red virtual, rellene la Tabla D. Colabore con su departamento de TI para determinar esta lista.</span><span class="sxs-lookup"><span data-stu-id="2b00b-193">For two Domain Name System (DNS) servers in your on-premises network that you want to use when initially setting up the domain controllers in your virtual network, fill in Table D. Work with your IT department to determine this list.</span></span>
  
|<span data-ttu-id="2b00b-194">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="2b00b-194">**Item**</span></span>|<span data-ttu-id="2b00b-195">**Nombre descriptivo del servidor DNS**</span><span class="sxs-lookup"><span data-stu-id="2b00b-195">**DNS server friendly name**</span></span>|<span data-ttu-id="2b00b-196">**Dirección IP del servidor DNS**</span><span class="sxs-lookup"><span data-stu-id="2b00b-196">**DNS server IP address**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="2b00b-197">1.</span><span class="sxs-lookup"><span data-stu-id="2b00b-197">1.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="2b00b-198">2.</span><span class="sxs-lookup"><span data-stu-id="2b00b-198">2.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="2b00b-199">**Tabla D: Servidores DNS locales**</span><span class="sxs-lookup"><span data-stu-id="2b00b-199">**Table D: On-premises DNS servers**</span></span>
  
<span data-ttu-id="2b00b-200">Para enrutar paquetes desde la red entre locales a la red de la organización a través de la conexión VPN de sitio a sitio, debe configurar la red virtual con una red local que tenga una lista de espacios de direcciones (en notación CIDR) para todos los disponibles. ubicaciones en la red local de su organización.</span><span class="sxs-lookup"><span data-stu-id="2b00b-200">To route packets from the cross-premises network to your organization network across the site-to-site VPN connection, you must configure the virtual network with a local network that has a list of the address spaces (in CIDR notation) for all of the reachable locations on your organization's on-premises network.</span></span> <span data-ttu-id="2b00b-201">La lista de espacios de direcciones que definen la red local tiene que ser única y no puede superponerse con el espacio de direcciones usado para otras redes virtuales ni otras redes locales.</span><span class="sxs-lookup"><span data-stu-id="2b00b-201">The list of address spaces that define your local network must be unique and must not overlap with the address space used for other virtual networks or other local networks.</span></span>
  
<span data-ttu-id="2b00b-p108">Para el conjunto de espacios de direcciones de la red local, rellene la Tabla L. Fíjese en que aparecen tres entradas en blanco, pero lo normal es que necesite más. Colabore con su departamento de TI para determinar esta lista de espacios de direcciones.</span><span class="sxs-lookup"><span data-stu-id="2b00b-p108">For the set of local network address spaces, fill in Table L. Note that three blank entries are listed but you will typically need more. Work with your IT department to determine this list of address spaces.</span></span>
  
|<span data-ttu-id="2b00b-204">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="2b00b-204">**Item**</span></span>|<span data-ttu-id="2b00b-205">**Espacio de direcciones de la red local**</span><span class="sxs-lookup"><span data-stu-id="2b00b-205">**Local network address space**</span></span>|
|:-----|:-----|
|<span data-ttu-id="2b00b-206">1.</span><span class="sxs-lookup"><span data-stu-id="2b00b-206">1.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="2b00b-207">2.</span><span class="sxs-lookup"><span data-stu-id="2b00b-207">2.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="2b00b-208">3.</span><span class="sxs-lookup"><span data-stu-id="2b00b-208">3.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="2b00b-209">**Tabla L: Prefijos de direcciones para la red local**</span><span class="sxs-lookup"><span data-stu-id="2b00b-209">**Table L: Address prefixes for the local network**</span></span>
  
<span data-ttu-id="2b00b-210">Ahora, empecemos a crear la infraestructura de Azure para hospedar la autenticación federada para Office 365.</span><span class="sxs-lookup"><span data-stu-id="2b00b-210">Now let's begin building the Azure infrastructure to host your federated authentication for Office 365.</span></span>
  
> [!NOTE]
> <span data-ttu-id="2b00b-p109">Los siguientes conjuntos de comandos utilizan la última versión de Azure PowerShell. Visite [Get started with Azure PowerShell cmdlets (Introducción a los cmdlets de Azure)](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span><span class="sxs-lookup"><span data-stu-id="2b00b-p109">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="2b00b-213">Primero, abra un símbolo del sistema de Azure PowerShell e inicie sesión con su cuenta.</span><span class="sxs-lookup"><span data-stu-id="2b00b-213">First, start an Azure PowerShell prompt and login to your account.</span></span>
  
```
Connect-AzAccount
```

<!--
> [!TIP]
> For a text file that has all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664). 
-->
  
<span data-ttu-id="2b00b-214">Obtenga su nombre de suscripción mediante el comando siguiente.</span><span class="sxs-lookup"><span data-stu-id="2b00b-214">Get your subscription name using the following command.</span></span>
  
```
Get-AzSubscription | Sort Name | Select Name
```

<span data-ttu-id="2b00b-215">Para las versiones anteriores de Azure PowerShell, use este comando en su lugar.</span><span class="sxs-lookup"><span data-stu-id="2b00b-215">For older versions of Azure PowerShell, use this command instead.</span></span>
  
```
Get-AzSubscription | Sort Name | Select SubscriptionName
```

<span data-ttu-id="2b00b-216">Configure su suscripción de Azure.</span><span class="sxs-lookup"><span data-stu-id="2b00b-216">Set your Azure subscription.</span></span> <span data-ttu-id="2b00b-217">Reemplace todo lo que haya entre las comillas, incluidos los \< caracteres y >, con el nombre correcto.</span><span class="sxs-lookup"><span data-stu-id="2b00b-217">Replace everything within the quotes, including the \< and > characters, with the correct name.</span></span>
  
```
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

<span data-ttu-id="2b00b-p111">Después, cree los grupos de recursos. Para determinar un conjunto único de nombres de grupos de recursos, use este comando para mostrar una lista de los grupos de recursos existentes.</span><span class="sxs-lookup"><span data-stu-id="2b00b-p111">Next, create the new resource groups. To determine a unique set of resource group names, use this command to list your existing resource groups.</span></span>
  
```
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="2b00b-220">Rellene la tabla siguiente para el conjunto de nombres de grupos de recursos únicos.</span><span class="sxs-lookup"><span data-stu-id="2b00b-220">Fill in the following table for the set of unique resource group names.</span></span>
  
|<span data-ttu-id="2b00b-221">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="2b00b-221">**Item**</span></span>|<span data-ttu-id="2b00b-222">**Nombre del grupo de recursos**</span><span class="sxs-lookup"><span data-stu-id="2b00b-222">**Resource group name**</span></span>|<span data-ttu-id="2b00b-223">**Finalidad**</span><span class="sxs-lookup"><span data-stu-id="2b00b-223">**Purpose**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="2b00b-224">1.</span><span class="sxs-lookup"><span data-stu-id="2b00b-224">1.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="2b00b-225">Controladores de dominio</span><span class="sxs-lookup"><span data-stu-id="2b00b-225">Domain controllers</span></span>  <br/> |
|<span data-ttu-id="2b00b-226">2.</span><span class="sxs-lookup"><span data-stu-id="2b00b-226">2.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="2b00b-227">Servidores de AD FS</span><span class="sxs-lookup"><span data-stu-id="2b00b-227">AD FS servers</span></span>  <br/> |
|<span data-ttu-id="2b00b-228">3.</span><span class="sxs-lookup"><span data-stu-id="2b00b-228">3.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="2b00b-229">Servidores proxy de aplicación web</span><span class="sxs-lookup"><span data-stu-id="2b00b-229">Web application proxy servers</span></span>  <br/> |
|<span data-ttu-id="2b00b-230">4.</span><span class="sxs-lookup"><span data-stu-id="2b00b-230">4.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="2b00b-231">Elementos de la infraestructura</span><span class="sxs-lookup"><span data-stu-id="2b00b-231">Infrastructure elements</span></span>  <br/> |
   
 <span data-ttu-id="2b00b-232">**Tabla R: Grupos de recursos**</span><span class="sxs-lookup"><span data-stu-id="2b00b-232">**Table R: Resource groups**</span></span>
  
<span data-ttu-id="2b00b-233">Cree el grupo de recursos con estos comandos.</span><span class="sxs-lookup"><span data-stu-id="2b00b-233">Create your new resource groups with these commands.</span></span>
  
```
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

<span data-ttu-id="2b00b-234">Después, cree la red virtual de Azure y sus subredes.</span><span class="sxs-lookup"><span data-stu-id="2b00b-234">Next, you create the Azure virtual network and its subnets.</span></span>
  
```
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

<span data-ttu-id="2b00b-235">A continuación, cree grupos de seguridad de red para cada subred que tenga máquinas virtuales.</span><span class="sxs-lookup"><span data-stu-id="2b00b-235">Next, you create network security groups for each subnet that has virtual machines.</span></span> <span data-ttu-id="2b00b-236">Para realizar el aislamiento de la subred, puede agregar reglas para tipos específicos de tráfico permitido o denegado para el grupo de seguridad de red de una subred.</span><span class="sxs-lookup"><span data-stu-id="2b00b-236">To perform subnet isolation, you can add rules for the specific types of traffic allowed or denied to the network security group of a subnet.</span></span>
  
```
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
```

<span data-ttu-id="2b00b-237">Después, use estos comandos para crear las puertas de enlace para la conexión VPN de sitio a sitio.</span><span class="sxs-lookup"><span data-stu-id="2b00b-237">Next, use these commands to create the gateways for the site-to-site VPN connection.</span></span>
  
```
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
> <span data-ttu-id="2b00b-238">La autenticación federada de los usuarios individuales no se basa en los recursos locales.</span><span class="sxs-lookup"><span data-stu-id="2b00b-238">Federated authentication of individual users does not rely on any on-premises resources.</span></span> <span data-ttu-id="2b00b-239">Sin embargo, si esta conexión VPN de sitio a sitio deja de estar disponible, los controladores de dominio de la red virtual no recibirán actualizaciones de las cuentas de usuario y los grupos realizados en Windows Server AD local.</span><span class="sxs-lookup"><span data-stu-id="2b00b-239">However, if this site-to-site VPN connection becomes unavailable, the domain controllers in the VNet will not receive updates to user accounts and groups made in the on-premises Windows Server AD.</span></span> <span data-ttu-id="2b00b-240">Para asegurarse de que esto no suceda, puede configurar la alta disponibilidad para la conexión VPN de sitio a sitio.</span><span class="sxs-lookup"><span data-stu-id="2b00b-240">To ensure this does not happen, you can configure high availability for your site-to-site VPN connection.</span></span> <span data-ttu-id="2b00b-241">Para obtener más información, consulte [Conectividad de red virtual a red virtual y con alta disponibilidad entre locales](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span><span class="sxs-lookup"><span data-stu-id="2b00b-241">For more information, see [Highly Available Cross-Premises and VNet-to-VNet Connectivity](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span></span>
  
<span data-ttu-id="2b00b-242">El paso siguiente es anotar la dirección IPv4 pública de Azure VPN Gateway para la red virtual después de ejecutar este comando:</span><span class="sxs-lookup"><span data-stu-id="2b00b-242">Next, record the public IPv4 address of the Azure VPN gateway for your virtual network from the display of this command:</span></span>
  
```
Get-AzPublicIpAddress -Name $publicGatewayVipName -ResourceGroupName $rgName
```

<span data-ttu-id="2b00b-p114">Después, configure el dispositivo VPN local para que se conecte a Azure VPN Gateway. Para obtener más información, vea [Configurar un dispositivo VPN](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span><span class="sxs-lookup"><span data-stu-id="2b00b-p114">Next, configure your on-premises VPN device to connect to the Azure VPN gateway. For more information, see [Configure your VPN device](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="2b00b-245">Para configurar el dispositivo VPN local necesita lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="2b00b-245">To configure your on-premises VPN device, you will need the following:</span></span>
  
- <span data-ttu-id="2b00b-246">La dirección IPv4 pública de Azure VPN Gateway.</span><span class="sxs-lookup"><span data-stu-id="2b00b-246">The public IPv4 address of the Azure VPN gateway.</span></span>
    
- <span data-ttu-id="2b00b-247">La clave precompartida IPsec para la conexión VPN de sitio a sitio (Tabla V, elemento 5, columna Valor).</span><span class="sxs-lookup"><span data-stu-id="2b00b-247">The IPsec pre-shared key for the site-to-site VPN connection (Table V - Item 5 - Value column).</span></span>
    
<span data-ttu-id="2b00b-p115">Después, asegúrese de que el espacio de direcciones de la red virtual sea accesible desde la red local. Para hacerlo, normalmente se agrega una ruta que se corresponde con el espacio de direcciones de la red virtual al dispositivo VPN y, después, se publica esa ruta para el resto de la infraestructura de enrutamiento de la red de la organización. Colabore con su departamento de TI para conocer cómo completar este procedimiento.</span><span class="sxs-lookup"><span data-stu-id="2b00b-p115">Next, ensure that the address space of the virtual network is reachable from your on-premises network. This is usually done by adding a route corresponding to the virtual network address space to your VPN device and then advertising that route to the rest of the routing infrastructure of your organization network. Work with your IT department to determine how to do this.</span></span>
  
<span data-ttu-id="2b00b-p116">Después, defina los nombres de los tres conjuntos de disponibilidad. Rellene la Tabla A. </span><span class="sxs-lookup"><span data-stu-id="2b00b-p116">Next, define the names of three availability sets. Fill out Table A.</span></span> 
  
|<span data-ttu-id="2b00b-253">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="2b00b-253">**Item**</span></span>|<span data-ttu-id="2b00b-254">**Objetivo**</span><span class="sxs-lookup"><span data-stu-id="2b00b-254">**Purpose**</span></span>|<span data-ttu-id="2b00b-255">**Nombre del conjunto de disponibilidad**</span><span class="sxs-lookup"><span data-stu-id="2b00b-255">**Availability set name**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="2b00b-256">1.</span><span class="sxs-lookup"><span data-stu-id="2b00b-256">1.</span></span>  <br/> |<span data-ttu-id="2b00b-257">Controladores de dominio</span><span class="sxs-lookup"><span data-stu-id="2b00b-257">Domain controllers</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="2b00b-258">2.</span><span class="sxs-lookup"><span data-stu-id="2b00b-258">2.</span></span>  <br/> |<span data-ttu-id="2b00b-259">Servidores de AD FS</span><span class="sxs-lookup"><span data-stu-id="2b00b-259">AD FS servers</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="2b00b-260">3.</span><span class="sxs-lookup"><span data-stu-id="2b00b-260">3.</span></span>  <br/> |<span data-ttu-id="2b00b-261">Servidores proxy de aplicación web</span><span class="sxs-lookup"><span data-stu-id="2b00b-261">Web application proxy servers</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="2b00b-262">**Tabla A: Conjuntos de disponibilidad**</span><span class="sxs-lookup"><span data-stu-id="2b00b-262">**Table A: Availability sets**</span></span>
  
<span data-ttu-id="2b00b-263">Necesitará estos nombres al crear las máquinas virtuales en las fases 2, 3 y 4.</span><span class="sxs-lookup"><span data-stu-id="2b00b-263">You will need these names when you create the virtual machines in phases 2, 3, and 4.</span></span>
  
<span data-ttu-id="2b00b-264">Cree los conjuntos de disponibilidad con estos comandos de Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2b00b-264">Create the new availability sets with these Azure PowerShell commands.</span></span>
  
```
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

<span data-ttu-id="2b00b-265">Esta es la configuración que se muestra después de la finalización correcta de esta fase.</span><span class="sxs-lookup"><span data-stu-id="2b00b-265">This is the configuration resulting from the successful completion of this phase.</span></span>
  
<span data-ttu-id="2b00b-266">**Fase 1: Infraestructura de Azure para la autenticación federada de alta disponibilidad para Office 365**</span><span class="sxs-lookup"><span data-stu-id="2b00b-266">**Phase 1: The Azure infrastructure for high availability federated authentication for Office 365**</span></span>

![Fase 1 de la autenticación federada de Office 365 de alta disponibilidad en Azure con la infraestructura de Azure](media/4e7ba678-07df-40ce-b372-021bf7fc91fa.png)
  
## <a name="next-step"></a><span data-ttu-id="2b00b-268">Paso siguiente</span><span class="sxs-lookup"><span data-stu-id="2b00b-268">Next step</span></span>

<span data-ttu-id="2b00b-269">Use [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) para continuar con la configuración de esta carga de trabajo.</span><span class="sxs-lookup"><span data-stu-id="2b00b-269">Use [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) to continue with the configuration of this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2b00b-270">Vea también</span><span class="sxs-lookup"><span data-stu-id="2b00b-270">See Also</span></span>

[<span data-ttu-id="2b00b-271">Implementar la autenticación federada de alta disponibilidad para Office 365 en Azure</span><span class="sxs-lookup"><span data-stu-id="2b00b-271">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="2b00b-272">Identidad federada para el entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="2b00b-272">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="2b00b-273">Adopción de la nube y soluciones híbridas</span><span class="sxs-lookup"><span data-stu-id="2b00b-273">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

<span data-ttu-id="2b00b-274">[Información sobre la identidad de Office 365 y Azure Active Directory](about-office-365-identity.md) .</span><span class="sxs-lookup"><span data-stu-id="2b00b-274">[Understanding Office 365 identity and Azure Active Directory](about-office-365-identity.md)</span></span>


