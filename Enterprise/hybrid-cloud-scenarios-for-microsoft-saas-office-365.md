---
title: Escenarios de nube híbrida para SaaS de Microsoft (Office 365)
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
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: 'Resumen: comprenda la arquitectura y los escenarios híbridos de las ofertas de la nube basadas en SaaS de Microsoft (Office 365).'
ms.openlocfilehash: 90b751e4bbea42d723961eb2ac339d23faf8c259
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487536"
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a><span data-ttu-id="f2fb9-103">Escenarios de nube híbrida para Microsoft SaaS (Office 365)</span><span class="sxs-lookup"><span data-stu-id="f2fb9-103">Hybrid cloud scenarios for Microsoft SaaS (Office 365)</span></span>

 <span data-ttu-id="f2fb9-104">**Resumen:** Comprenda la arquitectura y los escenarios híbridos de las ofertas de la nube basadas en SaaS de Microsoft (Office 365).</span><span class="sxs-lookup"><span data-stu-id="f2fb9-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's SaaS-based cloud offerings (Office 365).</span></span>
  
<span data-ttu-id="f2fb9-105">Combine las implementaciones locales de Exchange, SharePoint o Skype Empresarial con sus equivalentes de Office 365 como parte de una migración a la nube o estrategia de integración a largo plazo.</span><span class="sxs-lookup"><span data-stu-id="f2fb9-105">Combine on-premises deployments of Exchange, SharePoint, or Skype for Business with their counterparts in Office 365 as part of a cloud migration or long-term integration strategy.</span></span>
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a><span data-ttu-id="f2fb9-106">Arquitectura de escenario híbrido de SaaS de Microsoft</span><span class="sxs-lookup"><span data-stu-id="f2fb9-106">Microsoft SaaS hybrid scenario architecture</span></span>

<span data-ttu-id="f2fb9-107">En la figura 1, se muestra la arquitectura de escenarios híbridos basados en SaaS de Microsoft para Office 365.</span><span class="sxs-lookup"><span data-stu-id="f2fb9-107">Figure 1 shows the architecture of Microsoft SaaS-based hybrid scenarios for Office 365.</span></span>
  
<span data-ttu-id="f2fb9-108">**Figura 1: Escenarios híbridos basados en SaaS de Microsoft para Office 365**</span><span class="sxs-lookup"><span data-stu-id="f2fb9-108">**Figure 1: Microsoft SaaS-based hybrid scenarios for Office 365**</span></span>

![Escenarios híbridos basados en SaaS de Microsoft para Office 365](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS.png)
  
<span data-ttu-id="f2fb9-110">Para cada capa de la arquitectura:</span><span class="sxs-lookup"><span data-stu-id="f2fb9-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="f2fb9-111">Aplicaciones y escenarios</span><span class="sxs-lookup"><span data-stu-id="f2fb9-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="f2fb9-112">Existe una gran variedad de escenarios híbridos basados en SaaS, que se alinean con los productos de Office Server y sus equivalentes de Office 365:</span><span class="sxs-lookup"><span data-stu-id="f2fb9-112">There are a variety of SaaS-based hybrid scenarios, aligning around Office Server products and their Office 365 counterparts:</span></span>
    
  - <span data-ttu-id="f2fb9-113">Exchange Server combinado con Exchange Online (Exchange Server híbrido)</span><span class="sxs-lookup"><span data-stu-id="f2fb9-113">Exchange Server combined with Exchange Online (Exchange Server hybrid)</span></span>
    
  - <span data-ttu-id="f2fb9-114">Skype Empresarial Server combinado con Skype Empresarial Online y los nuevos escenarios PBX en la nube y Cloud Connector Edition</span><span class="sxs-lookup"><span data-stu-id="f2fb9-114">Skype for Business Server combined with Skype for Business Online and the new Cloud PBX and Cloud Connector Edition scenarios</span></span>
    
  - <span data-ttu-id="f2fb9-115">SharePoint Server 2019, SharePoint Server 2016 o SharePoint Server 2013 combinado con SharePoint Online (varios escenarios)</span><span class="sxs-lookup"><span data-stu-id="f2fb9-115">SharePoint Server 2019, SharePoint Server 2016, or SharePoint Server 2013 combined with SharePoint Online (multiple scenarios)</span></span>
    
    <span data-ttu-id="f2fb9-116">También existe Exchange Online con Skype Empresarial Server local, un escenario híbrido entre productos.</span><span class="sxs-lookup"><span data-stu-id="f2fb9-116">There is also Exchange Online with Skype for Business Server on-premises, a cross-product hybrid scenario.</span></span>
    
- <span data-ttu-id="f2fb9-117">Identidad</span><span class="sxs-lookup"><span data-stu-id="f2fb9-117">Identity</span></span>
    
    <span data-ttu-id="f2fb9-118">Puede incluir la sincronización de directorios con los servicios de dominio de Active Directory (AD DS) locales.</span><span class="sxs-lookup"><span data-stu-id="f2fb9-118">Can include directory synchronization with your on-premises Active Directory Domain Services (AD DS).</span></span> <span data-ttu-id="f2fb9-119">Como alternativa, puede configurar Azure AD para que se federe con un proveedor de identidades de terceros.</span><span class="sxs-lookup"><span data-stu-id="f2fb9-119">Alternately, you can configure Azure AD to federate with a third-party identity provider.</span></span>
    
- <span data-ttu-id="f2fb9-120">Red</span><span class="sxs-lookup"><span data-stu-id="f2fb9-120">Network</span></span>
    
    <span data-ttu-id="f2fb9-121">Consta de la canalización de Internet existente o de una conexión de ExpressRoute con emparejamiento de Microsoft para Office 365 o Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="f2fb9-121">Consists of either your existing Internet pipe or an ExpressRoute connection with Microsoft peering for Office 365 or Dynamics 365.</span></span>
    
- <span data-ttu-id="f2fb9-122">Local</span><span class="sxs-lookup"><span data-stu-id="f2fb9-122">On-premises</span></span>
    
    <span data-ttu-id="f2fb9-p102">Puede constar de los servidores existentes de Exchange, SharePoint y Skype Empresarial, que deberían estar actualizados a las versiones más recientes. Después, se pueden combinar con sus equivalentes de Office 365 para los escenarios híbridos.</span><span class="sxs-lookup"><span data-stu-id="f2fb9-p102">Can consist of existing servers for Exchange, SharePoint, and Skype for Business, which should be updated to their latest versions. You can then combine them with their Office 365 counterparts for hybrid scenarios.</span></span>
    
<span data-ttu-id="f2fb9-125">Configurar su propio entorno de pruebas y desarrollo de Office 365, consulte las [guías del laboratorio de pruebas de office 365](cloud-adoption-test-lab-guides-tlgs.md).</span><span class="sxs-lookup"><span data-stu-id="f2fb9-125">Set up your own Office 365 dev/test environment, see [Office 365 Test Lab Guides](cloud-adoption-test-lab-guides-tlgs.md).</span></span>
  
## <a name="skype-for-business-hybrid"></a><span data-ttu-id="f2fb9-126">Skype empresarial híbrido</span><span class="sxs-lookup"><span data-stu-id="f2fb9-126">Skype for Business Hybrid</span></span>

<span data-ttu-id="f2fb9-127">Skype empresarial híbrido le permite combinar una implementación local existente con Skype empresarial online.</span><span class="sxs-lookup"><span data-stu-id="f2fb9-127">Skype for Business Hybrid lets you combine an existing on-premises deployment with Skype for Business Online.</span></span> <span data-ttu-id="f2fb9-128">Algunos usuarios se alojan de forma local y otros en línea, pero todos comparten el mismo dominio de Protocolo de inicio de sesión (SIP) como, por ejemplo, contoso.com.</span><span class="sxs-lookup"><span data-stu-id="f2fb9-128">Some users are homed on-premises and some users are homed online, but the users share the same Session Initiation Protocol (SIP) domain, such as contoso.com.</span></span> <span data-ttu-id="f2fb9-129">Puede usar esta configuración híbrida para la migración de local a Office 365 con el tiempo, según su programación.</span><span class="sxs-lookup"><span data-stu-id="f2fb9-129">You can use this hybrid configuration to migrate from on-premises to Office 365 over time, on your schedule.</span></span> <span data-ttu-id="f2fb9-130">Skype empresarial también se puede integrar con [Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint).</span><span class="sxs-lookup"><span data-stu-id="f2fb9-130">Skype for Business can also be integrated with [Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint).</span></span>
  
<span data-ttu-id="f2fb9-131">**Figura 2: la configuración híbrida de Skype empresarial**</span><span class="sxs-lookup"><span data-stu-id="f2fb9-131">**Figure 2: The Skype for Business hybrid configuration**</span></span>

![La configuración híbrida de Skype empresarial](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB.png)
  
<span data-ttu-id="f2fb9-133">En la figura 2, se muestra la configuración híbrida de Skype empresarial, que consta de un grupo de servidores front-end local de Skype empresarial y un servidor perimetral que se comunica con Skype empresarial online en Office 365.</span><span class="sxs-lookup"><span data-stu-id="f2fb9-133">Figure 2 shows the Skype for Business hybrid configuration, consisting of an on-premises Skype for Business front end pool and edge server communicating with Skype for Business Online in Office 365.</span></span>
  
<span data-ttu-id="f2fb9-134">Para obtener más información, consulte [planear la conectividad híbrida entre Skype empresarial Server y Skype empresarial online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span><span class="sxs-lookup"><span data-stu-id="f2fb9-134">For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span></span>
    
## <a name="cloud-pbx-with-skype-for-business-server"></a><span data-ttu-id="f2fb9-135">PBX en la nube con Skype Empresarial Server</span><span class="sxs-lookup"><span data-stu-id="f2fb9-135">Cloud PBX with Skype for Business Server</span></span>

<span data-ttu-id="f2fb9-136">PBX en la nube con Skype empresarial Server le permite realizar la transición de una implementación local de Skype empresarial Server existente a una topología con conectividad de red telefónica conMutada (RTC) local.</span><span class="sxs-lookup"><span data-stu-id="f2fb9-136">Cloud PBX with Skype for Business Server lets you transition an existing Skype for Business Server on-premises deployment to a topology with on-premises Public Switched Telephone Network (PSTN) connectivity.</span></span> 
  
<span data-ttu-id="f2fb9-137">**Figura 3: PBX en la nube con Skype Empresarial Server**</span><span class="sxs-lookup"><span data-stu-id="f2fb9-137">**Figure 3: Cloud PBX with Skype for Business Server**</span></span>

![PBX en la nube con Skype Empresarial Server](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB-CloudPBX.png)
  
<span data-ttu-id="f2fb9-139">En la figura 3 se muestra la PBX en la nube con la configuración de Skype empresarial Server, que consta de una puerta de enlace de telecomunicaciones o PBX local existente, un servidor de Skype empresarial Server y la RTC conectada al PBX en la nube de Microsoft en Office 365, que incluye Skype empresarial Online.</span><span class="sxs-lookup"><span data-stu-id="f2fb9-139">Figure 3 shows the Cloud PBX with Skype for Business Server configuration, consisting of an on-premises existing PBX or Telco gateway, a Skype for Business Server, and the PSTN connected to the Microsoft Cloud PBX in Office 365, which includes Skype for Business Online.</span></span>
  
<span data-ttu-id="f2fb9-140">Los usuarios de la organización alojados en la nube pueden recibir servicios de central de conmutación (PBX) de la nube de Microsoft, que incluyen señalización y correo de voz, pero la conectividad RTC (tono de marcado) se proporciona a través de la Telefonía IP empresarial desde la implementación de Skype Empresarial Server local.</span><span class="sxs-lookup"><span data-stu-id="f2fb9-140">Users in the organization who are homed in the cloud can receive private branch exchange (PBX) services from the Microsoft cloud that include signaling and voicemail, but PSTN connectivity (dial tone) is provided through Enterprise Voice from your on-premises Skype for Business Server deployment.</span></span>
  
<span data-ttu-id="f2fb9-141">Este es un buen ejemplo de una configuración híbrida que permite migrar gradualmente a un servicio basado en la nube.</span><span class="sxs-lookup"><span data-stu-id="f2fb9-141">This is a great example of a hybrid configuration that lets you gradually migrate to a cloud-based service.</span></span> <span data-ttu-id="f2fb9-142">Puede conservar las capacidades de voz de los usuarios al comenzar a moverlos a Skype Empresarial Online.</span><span class="sxs-lookup"><span data-stu-id="f2fb9-142">You can retain your users' voice capabilities as you begin to move them to Skype for Business Online.</span></span> <span data-ttu-id="f2fb9-143">Puede mover los usuarios a su propio ritmo, con la seguridad de que sus características de voz seguirán sin importar dónde se alojen.</span><span class="sxs-lookup"><span data-stu-id="f2fb9-143">You can move your users at your own pace, knowing that their voice features will continue no matter where they are homed.</span></span> 
  
<span data-ttu-id="f2fb9-144">Para obtener más información, consulte [planear la conectividad híbrida entre Skype empresarial Server y Skype empresarial online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span><span class="sxs-lookup"><span data-stu-id="f2fb9-144">For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span></span>
  
<span data-ttu-id="f2fb9-145">Si aún no tiene ninguna implementación de Lync Server o Skype Empresarial Server, puede usar Skype Empresarial Cloud Connector Edition, un conjunto de máquinas virtuales (VM) empaquetadas que implementan la conectividad RTC local con PBX en la nube.</span><span class="sxs-lookup"><span data-stu-id="f2fb9-145">If you do not already have an existing Lync Server or Skype for Business Server deployment, you can use Skype for Business Cloud Connector Edition, a set of packaged virtual machines (VMs) that implement on-premises PSTN connectivity with Cloud PBX.</span></span>
  
<span data-ttu-id="f2fb9-146">Para obtener más información, consulte [Plan for Skype for Business Cloud Connector Edition](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).</span><span class="sxs-lookup"><span data-stu-id="f2fb9-146">For more information, see [Plan for Skype for Business Cloud Connector Edition](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).</span></span>

  
## <a name="sharepoint-hybrid"></a><span data-ttu-id="f2fb9-147">Entorno híbrido de SharePoint</span><span class="sxs-lookup"><span data-stu-id="f2fb9-147">SharePoint Hybrid</span></span>

<span data-ttu-id="f2fb9-148">SharePoint híbrido combina SharePoint Online en Office 365 con su granja de SharePoint local para ofrecer la mejor experiencia conectada de ambos mundos.</span><span class="sxs-lookup"><span data-stu-id="f2fb9-148">SharePoint hybrid combines SharePoint Online in Office 365 with your on-premises SharePoint farm for a best of both worlds, connected experience.</span></span>
  
<span data-ttu-id="f2fb9-149">**Figura 4: La configuración híbrida de SharePoint**</span><span class="sxs-lookup"><span data-stu-id="f2fb9-149">**Figure 4: The SharePoint hybrid configuration**</span></span>

![La configuración híbrida de SharePoint](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SP.png)
  
<span data-ttu-id="f2fb9-151">La figura 4 muestra la configuración híbrida de SharePoint, que consta de una granja de SharePoint local que se comunica con SharePoint Online en Office 365.</span><span class="sxs-lookup"><span data-stu-id="f2fb9-151">Figure 4 shows the SharePoint hybrid configuration, consisting of an on-premises SharePoint farm communicating with SharePoint Online in Office 365.</span></span>
  
<span data-ttu-id="f2fb9-152">Escenarios híbridos de SharePoint:</span><span class="sxs-lookup"><span data-stu-id="f2fb9-152">SharePoint hybrid scenarios:</span></span>
  
- [<span data-ttu-id="f2fb9-153">OneDrive para la Empresa híbrido</span><span class="sxs-lookup"><span data-stu-id="f2fb9-153">Hybrid OneDrive for Business</span></span>](https://docs.microsoft.com/SharePoint/hybrid/configure-hybrid-onedrive-for-businessroadmap)
    
- [<span data-ttu-id="f2fb9-154">B2B de extranet híbrida</span><span class="sxs-lookup"><span data-stu-id="f2fb9-154">Hybrid Extranet B2B</span></span>](https://docs.microsoft.com/sharepoint/create-b2b-extranet)
    
- [<span data-ttu-id="f2fb9-155">Búsqueda híbrida</span><span class="sxs-lookup"><span data-stu-id="f2fb9-155">Hybrid search</span></span>](https://docs.microsoft.com/SharePoint/hybrid/configure-cloud-hybrid-searchroadmap)
    
- [<span data-ttu-id="f2fb9-156">Perfiles híbridos</span><span class="sxs-lookup"><span data-stu-id="f2fb9-156">Hybrid profiles</span></span>](https://docs.microsoft.com/SharePoint/hybrid/plan-hybrid-profiles)
    
- [<span data-ttu-id="f2fb9-157">Selector híbrido</span><span class="sxs-lookup"><span data-stu-id="f2fb9-157">Hybrid Picker</span></span>](https://docs.microsoft.com/SharePoint/hybrid/hybrid-picker-in-the-sharepoint-online-admin-center)
    
    <span data-ttu-id="f2fb9-158">Es fácil habilitar escenarios híbridos mediante asistentes que automatizan la configuración híbrida, disponible desde el Centro de administración de SharePoint Online en Office 365.</span><span class="sxs-lookup"><span data-stu-id="f2fb9-158">It is easy to enable hybrid scenarios using the wizards that automate hybrid configuration, available from the SharePoint Online admin center in Office 365.</span></span>
    
- [<span data-ttu-id="f2fb9-159">Iniciador de aplicaciones híbrido extensible</span><span class="sxs-lookup"><span data-stu-id="f2fb9-159">Extensible hybrid app launcher</span></span>](https://docs.microsoft.com/SharePoint/hybrid/the-extensible-hybrid-app-launcher)
    
    <span data-ttu-id="f2fb9-160">Permite a los usuarios ver y usar las aplicaciones y experiencias de Office 365 Video y Delve en las páginas de su granja de SharePoint local.</span><span class="sxs-lookup"><span data-stu-id="f2fb9-160">Allows users to view and use Office 365 video and Delve apps and experiences within the pages of their on-premises SharePoint farm.</span></span>
    
<span data-ttu-id="f2fb9-161">Todos estos escenarios híbridos de SharePoint, excepto el iniciador de aplicaciones híbrido extensible, están disponibles para los usuarios de SharePoint 2016 y SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="f2fb9-161">All of these SharePoint hybrid scenarios, except the Extensible hybrid app launcher, are available for both SharePoint 2016 and SharePoint 2013 users.</span></span>
  
## <a name="exchange-server-2016-hybrid"></a><span data-ttu-id="f2fb9-162">Exchange Server 2016 híbrido</span><span class="sxs-lookup"><span data-stu-id="f2fb9-162">Exchange Server 2016 Hybrid</span></span>

<span data-ttu-id="f2fb9-163">Con Exchange Server 2016 híbrido, puede materializar los beneficios de Exchange Online en Office 365 para los usuarios en línea mientras los usuarios locales siguen usando la infraestructura existente de Exchange Server. </span><span class="sxs-lookup"><span data-stu-id="f2fb9-163">With Exchange Server 2016 Hybrid, you can realize the benefits of Exchange Online in Office 365 for online users while on-premises users continue to use existing Exchange Server infrastructure.</span></span> 
  
<span data-ttu-id="f2fb9-164">**Figura 5: La configuración híbrida de Exchange 2016**</span><span class="sxs-lookup"><span data-stu-id="f2fb9-164">**Figure 5: The Exchange 2016 hybrid configuration**</span></span>

![La configuración híbrida de Exchange 2016](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-EX.png)
  
<span data-ttu-id="f2fb9-166">La figura 5 muestra la configuración híbrida de Exchange 2016, que consta de los servidores de buzones de correo de Exchange locales que se comunican con la protección en línea de Exchange y los buzones en Office 365.</span><span class="sxs-lookup"><span data-stu-id="f2fb9-166">Figure 5 shows the Exchange 2016 hybrid configuration, consisting of on-premises Exchange mailbox servers communicating with Exchange Online Protection and mailboxes in Office 365.</span></span>
  
<span data-ttu-id="f2fb9-167">Algunos usuarios tienen un servidor de correo local y otros usan Exchange Online, pero todos comparten el mismo espacio de direcciones de correo. </span><span class="sxs-lookup"><span data-stu-id="f2fb9-167">Some users have an on-premises email server and some users use Exchange Online, but all users share the same e-mail address space.</span></span> 
  
<span data-ttu-id="f2fb9-168">Esta configuración híbrida:</span><span class="sxs-lookup"><span data-stu-id="f2fb9-168">This hybrid configuration:</span></span>
  
- <span data-ttu-id="f2fb9-169">Aprovecha la infraestructura existente de Exchange Server durante la migración a Exchange Online con el tiempo, según su programación.</span><span class="sxs-lookup"><span data-stu-id="f2fb9-169">Leverages your existing Exchange Server infrastructure while you migrate to Exchange Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="f2fb9-170">Permite admitir sitios remotos sin invertir en infraestructura de sucursales.</span><span class="sxs-lookup"><span data-stu-id="f2fb9-170">Allows you to support remote sites without investing in branch office infrastructure.</span></span>
    
- <span data-ttu-id="f2fb9-171">Permite enrutar el correo electrónico entrante de Internet a través de Exchange Online Protection en Office 365.</span><span class="sxs-lookup"><span data-stu-id="f2fb9-171">Allows you to route incoming Internet email through Exchange Online Protection in Office 365.</span></span>
    
- <span data-ttu-id="f2fb9-172">Satisface las necesidades de organizaciones multinacionales con subsidiarias que necesitan que los datos residan localmente.</span><span class="sxs-lookup"><span data-stu-id="f2fb9-172">Serves the needs of multinational organizations with subsidiaries that require data to reside on-premises.</span></span>
    
<span data-ttu-id="f2fb9-173">También puede integrar esta configuración híbrida con otras aplicaciones de Microsoft Office 365, como Skype Empresarial Online y SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="f2fb9-173">You can also integrate this hybrid configuration with other Microsoft Office 365 applications, including Skype for Business Online and SharePoint Online.</span></span>
  
<span data-ttu-id="f2fb9-174">Para obtener más información, consulte implementaciones híbridas de [Exchange Server](https://docs.microsoft.com/exchange/exchange-hybrid).</span><span class="sxs-lookup"><span data-stu-id="f2fb9-174">For more information, see [Exchange Server Hybrid Deployments](https://docs.microsoft.com/exchange/exchange-hybrid).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f2fb9-175">Vea también</span><span class="sxs-lookup"><span data-stu-id="f2fb9-175">See Also</span></span>

[<span data-ttu-id="f2fb9-176">Microsoft Hybrid Cloud para arquitectos profesionales</span><span class="sxs-lookup"><span data-stu-id="f2fb9-176">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="f2fb9-177">Recursos de arquitectura de TI de Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="f2fb9-177">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

