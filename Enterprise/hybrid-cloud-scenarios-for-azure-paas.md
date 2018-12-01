---
title: Escenarios de nube híbrida para PaaS de Azure
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
ms.assetid: 5f4f5d0d-4638-48e8-a517-bd804856b617
description: 'Resumen: Comprenda la arquitectura y los escenarios híbridos de las ofertas de nubes basadas en Plataforma como servicio (PaaS) de Microsoft en Azure.'
ms.openlocfilehash: e536d81b6b14b05bef49d7c91b0404faec64303b
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123337"
---
# <a name="hybrid-cloud-scenarios-for-azure-paas"></a><span data-ttu-id="d18d4-103">Escenarios de nube híbrida para PaaS de Azure</span><span class="sxs-lookup"><span data-stu-id="d18d4-103">Hybrid cloud scenarios for Azure PaaS</span></span>

 <span data-ttu-id="d18d4-104">**Resumen:** Comprenda la arquitectura y los escenarios híbridos de las ofertas de nubes basadas en Plataforma como servicio (PaaS) de Microsoft en Azure.</span><span class="sxs-lookup"><span data-stu-id="d18d4-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's Platform as a Service (PaaS)-based cloud offerings in Azure.</span></span>
  
<span data-ttu-id="d18d4-105">Combine datos locales o recursos de proceso con aplicaciones nuevas o convertidas que se ejecuten en PaaS de Azure, que puedan aprovechar el rendimiento, la confiabilidad y la escalabilidad de la nube, además de proporcionar soporte técnico mejorado para los usuarios móviles.</span><span class="sxs-lookup"><span data-stu-id="d18d4-105">Combine on-premises data or computing resources with new or converted applications running in Azure PaaS, which can take advantage of cloud performance, reliability, and scale and provide better support for mobile users.</span></span> 
  
## <a name="azure-paas-hybrid-scenario-architecture"></a><span data-ttu-id="d18d4-106">Arquitectura de escenario híbrido de PaaS de Azure</span><span class="sxs-lookup"><span data-stu-id="d18d4-106">Azure PaaS hybrid scenario architecture</span></span>

<span data-ttu-id="d18d4-107">En la figura 1, se muestra la arquitectura de escenarios híbridos basados en PaaS de Microsoft en Azure.</span><span class="sxs-lookup"><span data-stu-id="d18d4-107">Figure 1 shows the architecture of Microsoft PaaS-based hybrid scenarios in Azure.</span></span>
  
<span data-ttu-id="d18d4-108">**Figura 1: Escenarios híbridos basados en PaaS de Microsoft en Azure**</span><span class="sxs-lookup"><span data-stu-id="d18d4-108">**Figure 1: Microsoft PaaS-based hybrid scenarios in Azure**</span></span>

![Escenarios híbridos basados en PaaS de Microsoft en Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS.png)
  
<span data-ttu-id="d18d4-110">Para cada capa de la arquitectura:</span><span class="sxs-lookup"><span data-stu-id="d18d4-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="d18d4-111">Aplicaciones y escenarios</span><span class="sxs-lookup"><span data-stu-id="d18d4-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="d18d4-112">Una aplicación PaaS híbrida se ejecuta en Azure y usa los recursos de proceso o almacenamiento locales.</span><span class="sxs-lookup"><span data-stu-id="d18d4-112">A hybrid PaaS application runs in Azure and uses on-premises compute or storage resources.</span></span>
    
- <span data-ttu-id="d18d4-113">Identidad</span><span class="sxs-lookup"><span data-stu-id="d18d4-113">Identity</span></span>
    
    <span data-ttu-id="d18d4-114">Consta de la sincronización de directorios o la federación con un proveedor de identidades de terceros.</span><span class="sxs-lookup"><span data-stu-id="d18d4-114">Consists of either directory synchronization or federation with a third-party identity provider.</span></span>
    
- <span data-ttu-id="d18d4-115">Red</span><span class="sxs-lookup"><span data-stu-id="d18d4-115">Network</span></span>
    
    <span data-ttu-id="d18d4-p101">Consta de la canalización de Internet existente o de una conexión de ExpressRoute con emparejamiento público a PaaS de Azure. Debe incluir una forma para que la aplicación de PaaS de Azure tenga acceso al recurso de almacenamiento o proceso local.</span><span class="sxs-lookup"><span data-stu-id="d18d4-p101">Consists of either your existing Internet pipe or an ExpressRoute connection with public peering to Azure PaaS. You must include a way for the Azure PaaS application to access the on-premises compute or storage resource.</span></span>
    
- <span data-ttu-id="d18d4-118">Local</span><span class="sxs-lookup"><span data-stu-id="d18d4-118">On-premises</span></span>
    
    <span data-ttu-id="d18d4-119">Consta de infraestructura de identidad y seguridad, así como de aplicaciones de línea de negocio (LOB) o servidores de bases de datos existentes, a los que una aplicación PaaS de Azure puede tener acceso con seguridad.</span><span class="sxs-lookup"><span data-stu-id="d18d4-119">Consists of identity and security infrastructure and existing line of business (LOB) applications or database servers, which an Azure PaaS application can securely access.</span></span>
    
## <a name="azure-paas-hybrid-application"></a><span data-ttu-id="d18d4-120">Aplicación híbrida de PaaS de Azure</span><span class="sxs-lookup"><span data-stu-id="d18d4-120">Azure PaaS hybrid application</span></span>

<span data-ttu-id="d18d4-121">En la figura 2, se muestra la configuración de una aplicación híbrida que se ejecuta en Azure.</span><span class="sxs-lookup"><span data-stu-id="d18d4-121">Figure 2 shows the configuration of a hybrid application running in Azure.</span></span>
  
<span data-ttu-id="d18d4-122">**Figura 2: Aplicación híbrida basada en PaaS de Azure**</span><span class="sxs-lookup"><span data-stu-id="d18d4-122">**Figure 2: Azure PaaS-based hybrid application**</span></span>

![Aplicación híbrida basada en PaaS de Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps.png)
  
<span data-ttu-id="d18d4-p102">En la figura 2, una red local hospeda almacenamiento o aplicaciones en servidores y una red perimetral que contiene un servidor proxy. Está conectada a los servicios de PaaS de Azure en Internet o con una conexión de ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="d18d4-p102">In Figure 2, an on-premises network hosts storage or apps on servers and a DMZ containing a proxy server. It is connected to Azure PaaS services either over the Internet or with an ExpressRoute connection.</span></span>
  
<span data-ttu-id="d18d4-126">Para poner sus recursos de proceso o almacenamiento a disposición de la aplicación PaaS de Azure híbrida, una organización puede hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="d18d4-126">An organization can make its compute or storage resources available to the Azure PaaS hybrid application by:</span></span>
  
- <span data-ttu-id="d18d4-127">Hospedar el recurso en servidores de la red perimetral.</span><span class="sxs-lookup"><span data-stu-id="d18d4-127">Hosting the resource on servers in the DMZ.</span></span>
    
- <span data-ttu-id="d18d4-128">Hospedar un servidor proxy inverso en la red perimetral, que permite las solicitudes autenticadas, entrantes, basadas en HTTPS para el recurso ubicado de manera local.</span><span class="sxs-lookup"><span data-stu-id="d18d4-128">Hosting a reverse proxy server in the DMZ, which allows authenticated, inbound, HTTPS-based requests to the resource that is located on-premises.</span></span>
    
<span data-ttu-id="d18d4-129">La aplicación de Azure puede usar las credenciales de:</span><span class="sxs-lookup"><span data-stu-id="d18d4-129">The Azure app can use credentials from:</span></span>
  
- <span data-ttu-id="d18d4-130">Azure AD, que se pueden sincronizar con el proveedor de identidades local, como Windows Server AD.</span><span class="sxs-lookup"><span data-stu-id="d18d4-130">Azure AD, which can be synchronized with your on-premises identity provider, such as Windows Server AD.</span></span>
    
- <span data-ttu-id="d18d4-131">Un proveedor de identidades de terceros.</span><span class="sxs-lookup"><span data-stu-id="d18d4-131">A third-party identity provider.</span></span>
    
### <a name="example-azure-paas-hybrid-application"></a><span data-ttu-id="d18d4-132">Aplicación PaaS de Azure híbrida de ejemplo</span><span class="sxs-lookup"><span data-stu-id="d18d4-132">Example Azure PaaS hybrid application</span></span>

<span data-ttu-id="d18d4-133">En la figura 3, se muestra un ejemplo de aplicación híbrida que se ejecuta en Azure.</span><span class="sxs-lookup"><span data-stu-id="d18d4-133">Figure 3 shows an example hybrid application running in Azure.</span></span>
  
<span data-ttu-id="d18d4-134">**Figura 3: Un ejemplo de aplicación híbrida basada en PaaS de Azure**</span><span class="sxs-lookup"><span data-stu-id="d18d4-134">**Figure 3: An example Azure PaaS-based hybrid application**</span></span>

![Un ejemplo de aplicación híbrida basada en PaaS de Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps-Ex.png)
  
<span data-ttu-id="d18d4-p103">En la figura 3, una red local hospeda una aplicación LOB. PaaS de Azure hospeda una aplicación móvil personalizada. Un smartphone en Internet tiene acceso a la aplicación móvil personalizada en Azure, que envía solicitudes de datos a la aplicación LOB local.</span><span class="sxs-lookup"><span data-stu-id="d18d4-p103">In Figure 3, an on-premises network hosts an LOB app. Azure PaaS hosts a custom mobile app. A smartphone on the Internet accesses the custom mobile app in Azure, which sends data requests to the on-premises LOB app.</span></span>
  
<span data-ttu-id="d18d4-p104">Esta aplicación PaaS de Azure híbrida de ejemplo es una aplicación móvil personalizada que proporciona información de contacto actualizada de los empleados. El escenario híbrido completo consta de:</span><span class="sxs-lookup"><span data-stu-id="d18d4-p104">This example Azure PaaS hybrid application is a custom mobile app that provides up-to-date contact information on employees. The end-to-end hybrid scenario consists of:</span></span>
  
- <span data-ttu-id="d18d4-141">Una aplicación para smartphone que necesita credenciales locales validadas para funcionar.</span><span class="sxs-lookup"><span data-stu-id="d18d4-141">A smartphone app that requires validated, on-premises credentials to run.</span></span>
    
- <span data-ttu-id="d18d4-142">Una aplicación móvil personalizada que se ejecuta en PaaS de Azure, que solicita información sobre empleados específicos según las consultas de la aplicación para smartphone de un usuario.</span><span class="sxs-lookup"><span data-stu-id="d18d4-142">A custom mobile app running in Azure PaaS, which requests information about specific employees based on queries from a user's smartphone app.</span></span>
    
- <span data-ttu-id="d18d4-143">Un servidor proxy inverso en la red perimetral que valida la aplicación móvil personalizada y reenvía la solicitud.</span><span class="sxs-lookup"><span data-stu-id="d18d4-143">A reverse proxy server in the DMZ that validates the custom mobile app and forwards the request.</span></span>
    
- <span data-ttu-id="d18d4-144">Una granja de servidores de aplicaciones LOB que atiende la solicitud de contacto, sujeta a los permisos de la cuenta del usuario.</span><span class="sxs-lookup"><span data-stu-id="d18d4-144">An LOB application server farm that services the contact request, subject to the permissions of the user's account.</span></span>
    
<span data-ttu-id="d18d4-145">Dado que el proveedor de identidades local se ha sincronizado con Azure AD, la aplicación móvil personalizada y la aplicación LOB pueden validar el nombre de cuenta del usuario que realiza la solicitud.</span><span class="sxs-lookup"><span data-stu-id="d18d4-145">Because the on-premises identity provider has been synchronized with Azure AD, both the custom mobile app and the LOB app can validate the requesting user's account name.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d18d4-146">Vea también</span><span class="sxs-lookup"><span data-stu-id="d18d4-146">See Also</span></span>

[<span data-ttu-id="d18d4-147">Microsoft Hybrid Cloud para arquitectos profesionales</span><span class="sxs-lookup"><span data-stu-id="d18d4-147">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="d18d4-148">Recursos de arquitectura de TI de la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="d18d4-148">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

