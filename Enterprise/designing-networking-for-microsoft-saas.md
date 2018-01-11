---
title: "Diseño de redes para SaaS de Microsoft"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: 'Resumen: Aprenda a optimizar la red para tener acceso a los servicios de SaaS de Microsoft, como Office 365, Microsoft Intune y Dynamics 365.'
ms.openlocfilehash: 970d27e50e06f4d872de67589295c490aaa6e0e7
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2018
---
# <a name="designing-networking-for-microsoft-saas"></a><span data-ttu-id="34eaf-103">Diseño de redes para SaaS de Microsoft</span><span class="sxs-lookup"><span data-stu-id="34eaf-103">Designing networking for Microsoft SaaS</span></span>

 <span data-ttu-id="34eaf-104">**Resumen:** Aprenda a optimizar la red para tener acceso a los servicios de SaaS de Microsoft, como Office 365, Microsoft Intune y Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="34eaf-104">**Summary:** Understand how to optimize your network for access to Microsoft's SaaS services, including Office 365, Microsoft Intune, and Dynamics 365.</span></span>
  
<span data-ttu-id="34eaf-105">La optimización de la red para los servicios SaaS de Microsoft requiere un análisis exhaustivo del perímetro de Internet, los dispositivos cliente y las operaciones de TI típicas.</span><span class="sxs-lookup"><span data-stu-id="34eaf-105">Optimizing your network for Microsoft SaaS services requires careful analysis of your Internet edge, your client devices, and typical IT operations.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a><span data-ttu-id="34eaf-106">Pasos para preparar la red para los servicios SaaS de Microsoft</span><span class="sxs-lookup"><span data-stu-id="34eaf-106">Steps to prepare your network for Microsoft SaaS services</span></span>

<span data-ttu-id="34eaf-107">Siga estos pasos para optimizar la red para los servicios SaaS de Microsoft:</span><span class="sxs-lookup"><span data-stu-id="34eaf-107">Follow these steps to optimize your network for Microsoft SaaS services:</span></span>
  
1. <span data-ttu-id="34eaf-108">Vea la sección **Pasos para preparar la red para Servicios en la nube de Microsoft** en [Elementos comunes de conectividad de Microsoft Cloud](common-elements-of-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="34eaf-108">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="34eaf-109">Optimice la salida de Internet para los servicios SaaS de Microsoft siguiendo las recomendaciones del servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="34eaf-109">Optimize your Internet egress for Microsoft SaaS services using the proxy server recommendations.</span></span>
    
3. <span data-ttu-id="34eaf-110">Optimice el rendimiento de Internet siguiendo las recomendaciones de proximidad y ubicación.</span><span class="sxs-lookup"><span data-stu-id="34eaf-110">Optimize your Internet throughput using the proximity and location recommendations.</span></span>
    
4. <span data-ttu-id="34eaf-111">Optimice el rendimiento de los equipos cliente y la intranet en la que se encuentran siguiendo las consideraciones para el uso de clientes.</span><span class="sxs-lookup"><span data-stu-id="34eaf-111">Optimize the performance of your client computers and the intranet on which they are located using the client usage considerations.</span></span>
    
5. <span data-ttu-id="34eaf-112">Si es necesario, optimice el rendimiento de las migraciones de datos y la sincronización siguiendo las consideraciones de operaciones de TI.</span><span class="sxs-lookup"><span data-stu-id="34eaf-112">As needed, optimize the performance of data migrations and synchronization using the IT operations considerations.</span></span>
    
## <a name="internet-edge-considerations"></a><span data-ttu-id="34eaf-113">Consideraciones de perímetro de Internet</span><span class="sxs-lookup"><span data-stu-id="34eaf-113">Internet edge considerations</span></span>

<span data-ttu-id="34eaf-114">A continuación, indicamos algunos aspectos que tener en cuenta al optimizar el perímetro de Internet y el rendimiento de los servicios SaaS de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="34eaf-114">Here are some things to consider optimize your Internet edge and throughput to Microsoft SaaS services.</span></span>
  
<span data-ttu-id="34eaf-115">**Figura 1: Opciones de conexión de los servicios SaaS de Microsoft**</span><span class="sxs-lookup"><span data-stu-id="34eaf-115">**Figure 1: Connection options for Microsoft SaaS services**</span></span>

![Figura 1: Opciones de conexión de los servicios SaaS de Microsoft](images/Network_Poster/SaaS1.png)
  
<span data-ttu-id="34eaf-117">La figura 1 muestra una red local que se conecta a los servicios SaaS de Microsoft a través de una canalización de Internet o ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="34eaf-117">Figure 1 shows an on-premises network connecting to Microsoft SaaS services over an Internet pipe or ExpressRoute.</span></span>
  
<span data-ttu-id="34eaf-118">Estas son algunas recomendaciones para optimizar el servidor proxy:</span><span class="sxs-lookup"><span data-stu-id="34eaf-118">Here are some recommendations to optimize your proxy server:</span></span>
  
- <span data-ttu-id="34eaf-119">Configurar los clientes web con WPAD, PAC o GPO</span><span class="sxs-lookup"><span data-stu-id="34eaf-119">Configure web clients using WPAD, PAC, or GPO</span></span>
    
- <span data-ttu-id="34eaf-120">No usar la interceptación de SSL</span><span class="sxs-lookup"><span data-stu-id="34eaf-120">Don't use SSL interception</span></span>
    
- <span data-ttu-id="34eaf-121">Usar un archivo PAC con el fin de evitar el servidor proxy para los nombres DNS de los servicios SaaS de Microsoft</span><span class="sxs-lookup"><span data-stu-id="34eaf-121">Use a PAC file to bypass the proxy for Microsoft SaaS service DNS names</span></span>
    
- <span data-ttu-id="34eaf-122">Permitir el tráfico para la comprobación de CRL/OCSP</span><span class="sxs-lookup"><span data-stu-id="34eaf-122">Allow traffic for CRL/OCSP verification</span></span>
    
<span data-ttu-id="34eaf-123">Estos son algunos cuellos de botella del servidor proxy que se deben comprobar:</span><span class="sxs-lookup"><span data-stu-id="34eaf-123">Here are some proxy server bottlenecks to check:</span></span>
  
- <span data-ttu-id="34eaf-124">Conexiones persistentes insuficientes (Outlook)</span><span class="sxs-lookup"><span data-stu-id="34eaf-124">Insufficient persistent connections (Outlook)</span></span>
    
- <span data-ttu-id="34eaf-125">Capacidad insuficiente</span><span class="sxs-lookup"><span data-stu-id="34eaf-125">Insufficient capacity</span></span>
    
- <span data-ttu-id="34eaf-126">Realizar una evaluación fuera de red</span><span class="sxs-lookup"><span data-stu-id="34eaf-126">Doing off-network evaluation</span></span>
    
- <span data-ttu-id="34eaf-127">Requerir autenticación</span><span class="sxs-lookup"><span data-stu-id="34eaf-127">Requiring authentication</span></span>
    
- <span data-ttu-id="34eaf-128">No hay soporte para el tráfico UDP (Skype Empresarial)</span><span class="sxs-lookup"><span data-stu-id="34eaf-128">No support for UDP traffic (Skype for Business)</span></span>
    
<span data-ttu-id="34eaf-129">Estas son algunas recomendaciones sobre proximidad y ubicación:</span><span class="sxs-lookup"><span data-stu-id="34eaf-129">Here are some proximity and location recommendations:</span></span>
  
- <span data-ttu-id="34eaf-130">No enrutar el tráfico de Internet a través de la WAN privada</span><span class="sxs-lookup"><span data-stu-id="34eaf-130">Don't route your Internet traffic over the private WAN</span></span>
    
- <span data-ttu-id="34eaf-131">Usar el flujo de tráfico de DNS e Internet en la región para los usuarios de fuera de la región</span><span class="sxs-lookup"><span data-stu-id="34eaf-131">Use in-region DNS and Internet traffic flow for out-of-region users</span></span>
    
- <span data-ttu-id="34eaf-132">Usar ExpressRoute para un ancho de banda alto a Office 365 y la conectividad simultánea con los servicios de Azure</span><span class="sxs-lookup"><span data-stu-id="34eaf-132">Use ExpressRoute for high bandwidth to Office 365 and concurrent connectivity with Azure services</span></span>
    
<span data-ttu-id="34eaf-133">Estos son los puertos de salida necesarios para el tráfico de Office 365:</span><span class="sxs-lookup"><span data-stu-id="34eaf-133">Here are the outbound ports needed for Office 365 traffic:</span></span>
  
- <span data-ttu-id="34eaf-134">TCP 80 (para las comprobaciones CRL/OCSP)</span><span class="sxs-lookup"><span data-stu-id="34eaf-134">TCP 80 (for CRL/OCSP checks)</span></span>
    
- <span data-ttu-id="34eaf-135">TCP 443</span><span class="sxs-lookup"><span data-stu-id="34eaf-135">TCP 443</span></span>
    
- <span data-ttu-id="34eaf-136">UDP 3478</span><span class="sxs-lookup"><span data-stu-id="34eaf-136">UDP 3478</span></span>
    
- <span data-ttu-id="34eaf-137">TCP 5223</span><span class="sxs-lookup"><span data-stu-id="34eaf-137">TCP 5223</span></span>
    
- <span data-ttu-id="34eaf-138">TCP 50000-59999–59.999</span><span class="sxs-lookup"><span data-stu-id="34eaf-138">TCP 50000-59999</span></span>
    
- <span data-ttu-id="34eaf-139">UDP 50000-59999</span><span class="sxs-lookup"><span data-stu-id="34eaf-139">UDP 50000-59999</span></span>
    
## <a name="client-usage-considerations"></a><span data-ttu-id="34eaf-140">Consideraciones para el uso de clientes</span><span class="sxs-lookup"><span data-stu-id="34eaf-140">Client usage considerations</span></span>

<span data-ttu-id="34eaf-141">En primer lugar, configure el conjunto de servicios que los clientes van a usar, como:</span><span class="sxs-lookup"><span data-stu-id="34eaf-141">First, configure the set of services that your clients will be using, such as:</span></span>
  
- <span data-ttu-id="34eaf-142">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="34eaf-142">Azure Active Directory</span></span>
    
- <span data-ttu-id="34eaf-143">Office 365</span><span class="sxs-lookup"><span data-stu-id="34eaf-143">Office 365</span></span>
    
  - <span data-ttu-id="34eaf-144">Aplicaciones cliente de Office</span><span class="sxs-lookup"><span data-stu-id="34eaf-144">Office client apps</span></span>
    
  - <span data-ttu-id="34eaf-145">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="34eaf-145">SharePoint Online</span></span>
    
  - <span data-ttu-id="34eaf-146">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="34eaf-146">Exchange Online</span></span>
    
  - <span data-ttu-id="34eaf-147">Skype Empresarial</span><span class="sxs-lookup"><span data-stu-id="34eaf-147">Skype for Business</span></span>
    
- <span data-ttu-id="34eaf-148">Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="34eaf-148">Microsoft Intune</span></span>
    
- <span data-ttu-id="34eaf-149">Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="34eaf-149">Dynamics 365</span></span>
    
<span data-ttu-id="34eaf-150">En el caso de los equipos cliente, determine lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="34eaf-150">For your client computers, determine the following:</span></span>
  
- <span data-ttu-id="34eaf-151">Número máximo en cualquier momento (hora del días, estacional, picos y valles en el uso)</span><span class="sxs-lookup"><span data-stu-id="34eaf-151">Maximum number at any one time (time of day, seasonal, peaks and troughs in usage)</span></span>
    
- <span data-ttu-id="34eaf-152">Ancho de banda total necesaria para los picos</span><span class="sxs-lookup"><span data-stu-id="34eaf-152">Total bandwidth needed for peaks</span></span>
    
- <span data-ttu-id="34eaf-153">Latencia en el dispositivo de salida de Internet</span><span class="sxs-lookup"><span data-stu-id="34eaf-153">Latency to the Internet egress device</span></span>
    
- <span data-ttu-id="34eaf-154">País de origen frente a país de colocalización de centro de datos</span><span class="sxs-lookup"><span data-stu-id="34eaf-154">Country of origin vs. country of datacenter co-location</span></span>
    
<span data-ttu-id="34eaf-155">Para cada tipo de cliente (PC, smartphone, tableta), asegúrese de que está instalada la versión actual de lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="34eaf-155">For each type of client (PC, smartphone, tablet), ensure the current:</span></span>
  
- <span data-ttu-id="34eaf-156">Sistema operativo </span><span class="sxs-lookup"><span data-stu-id="34eaf-156">Operating system</span></span>
    
- <span data-ttu-id="34eaf-157">Explorador de Internet</span><span class="sxs-lookup"><span data-stu-id="34eaf-157">Internet browser</span></span>
    
- <span data-ttu-id="34eaf-158">TCP/IP, pila</span><span class="sxs-lookup"><span data-stu-id="34eaf-158">TCP/IP stack</span></span>
    
- <span data-ttu-id="34eaf-159">Hardware de red</span><span class="sxs-lookup"><span data-stu-id="34eaf-159">Network hardware</span></span>
    
- <span data-ttu-id="34eaf-160">Controladores de SO para el hardware de red</span><span class="sxs-lookup"><span data-stu-id="34eaf-160">OS drivers for network hardware</span></span>
    
- <span data-ttu-id="34eaf-161">Las actualizaciones y revisiones</span><span class="sxs-lookup"><span data-stu-id="34eaf-161">Updates and patches are installed</span></span>
    
<span data-ttu-id="34eaf-162">También puede optimizar el rendimiento de la conexión de intranet (por cable, de forma inalámbrica o por VPN).</span><span class="sxs-lookup"><span data-stu-id="34eaf-162">Additionally, optimize intranet connection throughput (wired, wireless, or VPN).</span></span>
  
<span data-ttu-id="34eaf-163">Para obtener más información, consulte [Compatibilidad de NAT con Office 365](https://support.office.com/article/NAT-support-with-Office-365-170e96ea-d65d-4e51-acac-1de56abe39b9).</span><span class="sxs-lookup"><span data-stu-id="34eaf-163">For more information, see [NAT support with Office 365](https://support.office.com/article/NAT-support-with-Office-365-170e96ea-d65d-4e51-acac-1de56abe39b9).</span></span>
  
<span data-ttu-id="34eaf-164">Para conocer las recomendaciones más recientes para el uso de ExpressRoute con Office 365, consulte [Azure ExpressRoute para Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).</span><span class="sxs-lookup"><span data-stu-id="34eaf-164">For the latest recommendations for using ExpressRoute with Office 365, see [ExpressRoute for Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).</span></span>
  
<span data-ttu-id="34eaf-165">Para optimizar el rendimiento de la intranet, haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="34eaf-165">To optimize your intranet performance, do the following:</span></span>
  
- <span data-ttu-id="34eaf-166">Use herramientas para medir los tiempos de ida y vuelta (RTT) de los dispositivos perimetrales de Internet (PsPing, Ping, Tracert, TraceTCP, Monitor de red)</span><span class="sxs-lookup"><span data-stu-id="34eaf-166">Use tools to gauge round trip times (RTTs) to your Internet edge devices (PsPing, Ping, Tracert, TraceTCP, Network Monitor)</span></span>
    
- <span data-ttu-id="34eaf-167">Realice análisis de ruta de acceso de salida mediante protocolos de flujo</span><span class="sxs-lookup"><span data-stu-id="34eaf-167">Perform egress path analysis using flow protocols</span></span>
    
- <span data-ttu-id="34eaf-168">Realice análisis de dispositivos intermedios (antigüedad, mantenimiento, etc.)</span><span class="sxs-lookup"><span data-stu-id="34eaf-168">Perform analysis of intermediate devices (age, health, etc.)</span></span>
    
<span data-ttu-id="34eaf-169">Para obtener más información, consulte la [Herramienta PsPing](https://technet.microsoft.com/sysinternals/jj729731.aspx).</span><span class="sxs-lookup"><span data-stu-id="34eaf-169">For more information, see the [PsPing tool](https://technet.microsoft.com/sysinternals/jj729731.aspx).</span></span>
  
## <a name="it-operations-considerations"></a><span data-ttu-id="34eaf-170">Consideraciones sobre las operaciones de TI</span><span class="sxs-lookup"><span data-stu-id="34eaf-170">IT operations considerations</span></span>

<span data-ttu-id="34eaf-171">A continuación, describimos algunos factores que se deben considerar cuando se trabaja con una carga de trabajo de TI en un servicio SaaS de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="34eaf-171">Here are some things to consider when operating an IT workload in a Microsoft SaaS service.</span></span>
  
### <a name="one-time-migrations"></a><span data-ttu-id="34eaf-172">Migraciones únicas</span><span class="sxs-lookup"><span data-stu-id="34eaf-172">One-time migrations</span></span>

<span data-ttu-id="34eaf-173">La transferencia de datos masiva en aplicaciones basadas en la nube o el almacenamiento de archivado son ejemplos de migraciones únicas.</span><span class="sxs-lookup"><span data-stu-id="34eaf-173">Examples of one-time migrations are bulk data transfer for cloud-based applications or archival storage.</span></span>
  
<span data-ttu-id="34eaf-174">Si quiere optimizar la red durante las migraciones únicas:</span><span class="sxs-lookup"><span data-stu-id="34eaf-174">To optimize your network for on-time migrations:</span></span>
  
- <span data-ttu-id="34eaf-175">Evite el uso de la red en horas pico y en las horas de aplicación de revisiones en el equipo</span><span class="sxs-lookup"><span data-stu-id="34eaf-175">Avoid peak network usage and computer patching times</span></span>
    
- <span data-ttu-id="34eaf-176">La red se debe someter a pruebas piloto y de línea base, evalúe el mantenimiento de la red y resuelva los problemas antes de llevar a cabo la migración</span><span class="sxs-lookup"><span data-stu-id="34eaf-176">Should be baselined and piloted, assess network health and resolve issues before attempting actual migration</span></span>
    
- <span data-ttu-id="34eaf-177">Realice análisis finales para futuras migraciones</span><span class="sxs-lookup"><span data-stu-id="34eaf-177">Perform post-mortem for future migrations</span></span>
    
### <a name="ongoing-synchronizations"></a><span data-ttu-id="34eaf-178">Sincronizaciones continuas</span><span class="sxs-lookup"><span data-stu-id="34eaf-178">Ongoing synchronizations</span></span>

<span data-ttu-id="34eaf-179">Algunos ejemplos de sincronizaciones continuas son los archivos, la configuración o la información de directorio.</span><span class="sxs-lookup"><span data-stu-id="34eaf-179">Examples of ongoing synchronizations are directory information, settings, or files.</span></span>
  
<span data-ttu-id="34eaf-180">Si quiere optimizar la red en las sincronizaciones continuas:</span><span class="sxs-lookup"><span data-stu-id="34eaf-180">To optimize your network for ongoing synchronizations:</span></span>
  
- <span data-ttu-id="34eaf-181">Asegúrese de que se implante un sistema de supervisión del ancho de banda de la red y resuelva o descarte los errores encontrados</span><span class="sxs-lookup"><span data-stu-id="34eaf-181">Ensure that a network bandwidth monitoring system is in place, resolve or dismiss collected errors</span></span>
    
- <span data-ttu-id="34eaf-182">Use los resultados de la supervisión del ancho de banda para identificar la necesidad de cambios en la red (escalar vertical u horizontalmente, nuevos circuitos o adición de dispositivos)</span><span class="sxs-lookup"><span data-stu-id="34eaf-182">Use bandwidth monitoring results to determine need for network changes (scale-up/out, new circuits, or adding devices)</span></span>
    
<span data-ttu-id="34eaf-183">Para más información, visite:</span><span class="sxs-lookup"><span data-stu-id="34eaf-183">For more information, see:</span></span>
  
- <span data-ttu-id="34eaf-184">[Planeación de la migración y red para Office 365](https://aka.ms/tune)</span><span class="sxs-lookup"><span data-stu-id="34eaf-184">[Network and migration planning for Office 365](https://aka.ms/tune)</span></span>
    
- <span data-ttu-id="34eaf-185">[Curso de Microsoft Virtual Academy sobre la administración del rendimiento de Office 365](https://aka.ms/o365perf)</span><span class="sxs-lookup"><span data-stu-id="34eaf-185">[Office 365 Performance Management Microsoft Virtual Academy course](https://aka.ms/o365perf)</span></span>
    
- <span data-ttu-id="34eaf-186">[ExpressRoute para Office 365](https://aka.ms/expressrouteoffice365)</span><span class="sxs-lookup"><span data-stu-id="34eaf-186">[ExpressRoute for Office 365](https://aka.ms/expressrouteoffice365)</span></span>
    
## <a name="see-also"></a><span data-ttu-id="34eaf-187">Consulte también</span><span class="sxs-lookup"><span data-stu-id="34eaf-187">See Also</span></span>

[<span data-ttu-id="34eaf-188">Microsoft Cloud Networking para arquitectos profesionales</span><span class="sxs-lookup"><span data-stu-id="34eaf-188">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="34eaf-189">Recursos de arquitectura de TI de la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="34eaf-189">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

<span data-ttu-id="34eaf-190">[Mapa de ruta de Enterprise Cloud de Microsoft: Recursos para los responsables de decisiones de TI](https://sway.com/FJ2xsyWtkJc2taRD)</span><span class="sxs-lookup"><span data-stu-id="34eaf-190">[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://sway.com/FJ2xsyWtkJc2taRD)</span></span>



