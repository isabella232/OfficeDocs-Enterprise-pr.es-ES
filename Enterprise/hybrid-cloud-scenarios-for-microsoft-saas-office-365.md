---
title: Escenarios de nube híbrida para SaaS de Microsoft (Office 365)
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: 'Resumen: Conozca la arquitectura híbrida y los escenarios de Microsoft basada en SaaS (Office 365) de las ofertas de nube.'
ms.openlocfilehash: 53187d53b55eedf1fca4f0b98e34accf454c67df
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915595"
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a><span data-ttu-id="29f28-103">Escenarios de nube híbrida para Microsoft SaaS (Office 365)</span><span class="sxs-lookup"><span data-stu-id="29f28-103">Hybrid cloud scenarios for Microsoft SaaS (Office 365)</span></span>

 <span data-ttu-id="29f28-104">**Resumen:** Comprender la arquitectura híbrida y los escenarios de Microsoft basada en SaaS (Office 365) de las ofertas de nube.</span><span class="sxs-lookup"><span data-stu-id="29f28-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's SaaS-based cloud offerings (Office 365).</span></span>
  
<span data-ttu-id="29f28-105">Combine las implementaciones locales de Exchange, SharePoint o Skype Empresarial con sus equivalentes de Office 365 como parte de una migración a la nube o estrategia de integración a largo plazo.</span><span class="sxs-lookup"><span data-stu-id="29f28-105">Combine on-premises deployments of Exchange, SharePoint, or Skype for Business with their counterparts in Office 365 as part of a cloud migration or long-term integration strategy.</span></span>
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a><span data-ttu-id="29f28-106">Arquitectura de escenario híbrido de SaaS de Microsoft</span><span class="sxs-lookup"><span data-stu-id="29f28-106">Microsoft SaaS hybrid scenario architecture</span></span>

<span data-ttu-id="29f28-107">En la figura 1, se muestra la arquitectura de escenarios híbridos basados en SaaS de Microsoft para Office 365.</span><span class="sxs-lookup"><span data-stu-id="29f28-107">Figure 1 shows the architecture of Microsoft SaaS-based hybrid scenarios for Office 365.</span></span>
  
<span data-ttu-id="29f28-108">**Figura 1: Escenarios híbridos basados en SaaS de Microsoft para Office 365**</span><span class="sxs-lookup"><span data-stu-id="29f28-108">**Figure 1: Microsoft SaaS-based hybrid scenarios for Office 365**</span></span>

![Escenarios híbridos basados en SaaS de Microsoft para Office 365](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS.png)
  
<span data-ttu-id="29f28-110">Para cada capa de la arquitectura:</span><span class="sxs-lookup"><span data-stu-id="29f28-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="29f28-111">Aplicaciones y escenarios</span><span class="sxs-lookup"><span data-stu-id="29f28-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="29f28-112">Existe una gran variedad de escenarios híbridos basados en SaaS, que se alinean con los productos de Office Server y sus equivalentes de Office 365:</span><span class="sxs-lookup"><span data-stu-id="29f28-112">There are a variety of SaaS-based hybrid scenarios, aligning around Office Server products and their Office 365 counterparts:</span></span>
    
  - <span data-ttu-id="29f28-113">Exchange Server combinado con Exchange Online (Exchange Server híbrido)</span><span class="sxs-lookup"><span data-stu-id="29f28-113">Exchange Server combined with Exchange Online (Exchange Server hybrid)</span></span>
    
  - <span data-ttu-id="29f28-114">Skype Empresarial Server combinado con Skype Empresarial Online y los nuevos escenarios PBX en la nube y Cloud Connector Edition</span><span class="sxs-lookup"><span data-stu-id="29f28-114">Skype for Business Server combined with Skype for Business Online and the new Cloud PBX and Cloud Connector Edition scenarios</span></span>
    
  - <span data-ttu-id="29f28-115">SharePoint Server 2016 o SharePoint Server 2013 combinado con SharePoint Online (varios escenarios)</span><span class="sxs-lookup"><span data-stu-id="29f28-115">SharePoint Server 2016 or SharePoint Server 2013 combined with SharePoint Online (multiple scenarios)</span></span>
    
    <span data-ttu-id="29f28-116">También existe Exchange Online con Skype Empresarial Server local, un escenario híbrido entre productos.</span><span class="sxs-lookup"><span data-stu-id="29f28-116">There is also Exchange Online with Skype for Business Server on-premises, a cross-product hybrid scenario.</span></span>
    
- <span data-ttu-id="29f28-117">Identidad</span><span class="sxs-lookup"><span data-stu-id="29f28-117">Identity</span></span>
    
    <span data-ttu-id="29f28-p101">Puede incluir la sincronización de directorios con Windows Server AD local. Como alternativa, puede configurar Azure AD para que se federe con un proveedor de identidades de terceros.</span><span class="sxs-lookup"><span data-stu-id="29f28-p101">Can include directory synchronization with your on-premises Windows Server AD. Alternately, you can configure Azure AD to federate with a third-party identity provider.</span></span>
    
- <span data-ttu-id="29f28-120">Red</span><span class="sxs-lookup"><span data-stu-id="29f28-120">Network</span></span>
    
    <span data-ttu-id="29f28-121">Consta de la canalización de Internet existente o de una conexión de ExpressRoute con emparejamiento de Microsoft para Office 365 o Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="29f28-121">Consists of either your existing Internet pipe or an ExpressRoute connection with Microsoft peering for Office 365 or Dynamics 365.</span></span>
    
- <span data-ttu-id="29f28-122">Local</span><span class="sxs-lookup"><span data-stu-id="29f28-122">On-premises</span></span>
    
    <span data-ttu-id="29f28-p102">Puede constar de los servidores existentes de Exchange, SharePoint y Skype Empresarial, que deberían estar actualizados a las versiones más recientes. Después, se pueden combinar con sus equivalentes de Office 365 para los escenarios híbridos.</span><span class="sxs-lookup"><span data-stu-id="29f28-p102">Can consist of existing servers for Exchange, SharePoint, and Skype for Business, which should be updated to their latest versions. You can then combine them with their Office 365 counterparts for hybrid scenarios.</span></span>
    
<span data-ttu-id="29f28-125">Configure su propio [Office 365 dev/test environment](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="29f28-125">Set up your own [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
## <a name="skype-for-business-2015-hybrid"></a><span data-ttu-id="29f28-126">Skype Empresarial 2015 híbrido</span><span class="sxs-lookup"><span data-stu-id="29f28-126">Skype for Business 2015 Hybrid</span></span>

<span data-ttu-id="29f28-p103">Skype para profesionales 2015 híbrido le permite combinar una implementación local existente con Skype para profesionales en línea. Algunos usuarios son alojarse en local y algunos usuarios están hospedados en línea, pero los usuarios comparten el mismo dominio de protocolo de inicio de sesión (SIP), por ejemplo, contoso.com. Puede usar esta configuración híbrida para migrar de local a Office 365 con el tiempo, en la programación. Skype para 2015 empresarial también se puede integrar con Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="29f28-p103">Skype for Business 2015 Hybrid allows you to combine an existing on-premises deployment with Skype for Business Online. Some users are homed on-premises and some users are homed online, but the users share the same Session Initiation Protocol (SIP) domain, such as contoso.com. You can use this hybrid configuration to migrate from on-premises to Office 365 over time, on your schedule. Skype for Business 2015 can also be integrated with Exchange Online.</span></span>
  
<span data-ttu-id="29f28-131">**Figura 2: La configuración híbrida de Skype Empresarial 2015**</span><span class="sxs-lookup"><span data-stu-id="29f28-131">**Figure 2: The Skype for Business 2015 hybrid configuration**</span></span>

![La configuración híbrida de Skype Empresarial 2015](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB.png)
  
<span data-ttu-id="29f28-133">La figura 2 muestra la Skype para la configuración híbrida de negocio 2015, formado por un Skype local para el grupo de servidores de negocio 2015 front-end y servidor perimetral comunicarse con Skype para profesionales en línea en Office 365.</span><span class="sxs-lookup"><span data-stu-id="29f28-133">Figure 2 shows the Skype for Business 2015 hybrid configuration, consisting of an on-premises Skype for Business 2015 front end pool and edge server communicating with Skype for Business Online in Office 365.</span></span>
  
<span data-ttu-id="29f28-134">Para obtener más información, vea:</span><span class="sxs-lookup"><span data-stu-id="29f28-134">For more information, see:</span></span>
  
- [<span data-ttu-id="29f28-135">Planeación de la conectividad híbrida entre Skype para Business Server y Skype para profesionales en línea</span><span class="sxs-lookup"><span data-stu-id="29f28-135">Plan hybrid connectivity between Skype for Business Server and Skype for Business Online</span></span>](https://technet.microsoft.com/library/jj205403.aspx)
    
- [<span data-ttu-id="29f28-136">Configuraciones de híbridas compatibles para Skype para Business Server 2015</span><span class="sxs-lookup"><span data-stu-id="29f28-136">Supported hybrid configurations for Skype for Business Server 2015</span></span>](https://technet.microsoft.com/library/jj945633.aspx)
    
- [<span data-ttu-id="29f28-137">Skype para entornos híbridos de negocio</span><span class="sxs-lookup"><span data-stu-id="29f28-137">Skype for Business Hybrid</span></span>](http://hybrid.office.com/skype-for-business/)
    
## <a name="cloud-pbx-with-skype-for-business-server"></a><span data-ttu-id="29f28-138">PBX en la nube con Skype Empresarial Server</span><span class="sxs-lookup"><span data-stu-id="29f28-138">Cloud PBX with Skype for Business Server</span></span>

<span data-ttu-id="29f28-139">PBX en la nube con Skype Empresarial Server permite realizar la transición de una implementación local de Skype Empresarial Server existente a una topología con conectividad de red telefónica conmutada (RTC) local. </span><span class="sxs-lookup"><span data-stu-id="29f28-139">Cloud PBX with Skype for Business Server allows you to transition an existing Skype for Business Server on-premises deployment to a topology with on-premises Public Switched Telephone Network (PSTN) connectivity.</span></span> 
  
<span data-ttu-id="29f28-140">**Figura 3: PBX en la nube con Skype Empresarial Server**</span><span class="sxs-lookup"><span data-stu-id="29f28-140">**Figure 3: Cloud PBX with Skype for Business Server**</span></span>

![PBX en la nube con Skype Empresarial Server](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB-CloudPBX.png)
  
<span data-ttu-id="29f28-142">La figura 3 muestra la PBX en la nube con Skype para la configuración de servidor de negocio, que consta de un sistema PBX existente o puerta de enlace de telecomunicaciones, un Skype para Business Server y la RTC conectado a la PBX de nube de Microsoft en Office 365, que incluye Skype para la empresa-locales En línea.</span><span class="sxs-lookup"><span data-stu-id="29f28-142">Figure 3 shows the Cloud PBX with Skype for Business Server configuration, consisting of an on-premises existing PBX or Telco gateway, a Skype for Business Server, and the PSTN connected to the Microsoft Cloud PBX in Office 365, which includes Skype for Business Online.</span></span>
  
<span data-ttu-id="29f28-143">Los usuarios de la organización alojados en la nube pueden recibir servicios de central de conmutación (PBX) de la nube de Microsoft, que incluyen señalización y correo de voz, pero la conectividad RTC (tono de marcado) se proporciona a través de la Telefonía IP empresarial desde la implementación de Skype Empresarial Server local.</span><span class="sxs-lookup"><span data-stu-id="29f28-143">Users in the organization who are homed in the cloud can receive private branch exchange (PBX) services from the Microsoft cloud that include signaling and voicemail, but PSTN connectivity (dial tone) is provided through Enterprise Voice from your on-premises Skype for Business Server deployment.</span></span>
  
<span data-ttu-id="29f28-p104">Este es un gran ejemplo de una configuración híbrida que le permite migrar a un servicio basado en la nube de forma gradual. Puede conservar las capacidades de voz de los usuarios al comenzar a moverlos a Skype Empresarial Online. Puede mover los usuarios a su propio ritmo, con la seguridad de que sus características de voz seguirán sin importar dónde se alojen. </span><span class="sxs-lookup"><span data-stu-id="29f28-p104">This is a great example of a hybrid configuration that allows you to gradually migrate to a cloud-based service. You can retain your users' voice capabilities as you begin to move them to Skype for Business Online. You can move your users at your own pace, knowing that their voice features will continue no matter where they are homed.</span></span> 
  
<span data-ttu-id="29f28-147">Para obtener más información, consulte [Plan de conectividad híbrida entre Skype para Business Server y Skype para profesionales Online o Lync Server 2013](https://technet.microsoft.com/library/jj205403.aspx).</span><span class="sxs-lookup"><span data-stu-id="29f28-147">For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online or Lync Server 2013](https://technet.microsoft.com/library/jj205403.aspx).</span></span>
  
<span data-ttu-id="29f28-148">Si aún no tiene ninguna implementación de Lync Server o Skype Empresarial Server, puede usar Skype Empresarial Cloud Connector Edition, un conjunto de máquinas virtuales (VM) empaquetadas que implementan la conectividad RTC local con PBX en la nube.</span><span class="sxs-lookup"><span data-stu-id="29f28-148">If you do not already have an existing Lync Server or Skype for Business Server deployment, you can use Skype for Business Cloud Connector Edition, a set of packaged virtual machines (VMs) that implement on-premises PSTN connectivity with Cloud PBX.</span></span>
  
<span data-ttu-id="29f28-149">Para obtener más información, consulte [Plan de Skype para Business Edition de conector en la nube](https://technet.microsoft.com/library/mt605227.aspx).</span><span class="sxs-lookup"><span data-stu-id="29f28-149">For more information, see [Plan for Skype for Business Cloud Connector Edition](https://technet.microsoft.com/library/mt605227.aspx).</span></span>
  
## <a name="sharepoint-hybrid"></a><span data-ttu-id="29f28-150">Entorno híbrido de SharePoint</span><span class="sxs-lookup"><span data-stu-id="29f28-150">SharePoint Hybrid</span></span>

<span data-ttu-id="29f28-151">SharePoint híbrido combina SharePoint Online en Office 365 con su granja de SharePoint local para ofrecer la mejor experiencia conectada de ambos mundos.</span><span class="sxs-lookup"><span data-stu-id="29f28-151">SharePoint hybrid combines SharePoint Online in Office 365 with your on-premises SharePoint farm for a best of both worlds, connected experience.</span></span>
  
<span data-ttu-id="29f28-152">**Figura 4: La configuración híbrida de SharePoint**</span><span class="sxs-lookup"><span data-stu-id="29f28-152">**Figure 4: The SharePoint hybrid configuration**</span></span>

![La configuración híbrida de SharePoint](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SP.png)
  
<span data-ttu-id="29f28-154">La figura 4 muestra la configuración híbrida de SharePoint, que consta de una granja de servidores de SharePoint local comunicarse con SharePoint Online en Office 365.</span><span class="sxs-lookup"><span data-stu-id="29f28-154">Figure 4 shows the SharePoint hybrid configuration, consisting of an on-premises SharePoint farm communicating with SharePoint Online in Office 365.</span></span>
  
<span data-ttu-id="29f28-155">Escenarios híbridos de SharePoint:</span><span class="sxs-lookup"><span data-stu-id="29f28-155">SharePoint hybrid scenarios:</span></span>
  
- [<span data-ttu-id="29f28-156">OneDrive para la Empresa híbrido</span><span class="sxs-lookup"><span data-stu-id="29f28-156">Hybrid OneDrive for Business</span></span>](https://technet.microsoft.com/library/mt147425%28v=office.16%29.aspx)
    
- [<span data-ttu-id="29f28-157">Sitios de grupo híbrida</span><span class="sxs-lookup"><span data-stu-id="29f28-157">Hybrid team sites</span></span>](https://technet.microsoft.com/library/mt346110%28v=office.16%29.aspx)
    
- [<span data-ttu-id="29f28-158">B2B Extranet híbrida</span><span class="sxs-lookup"><span data-stu-id="29f28-158">Hybrid Extranet B2B</span></span>](https://support.office.com/article/SharePoint-Business-to-Business-Collaboration-Extranet-for-Partners-with-Office-365-7b087413-165a-4e94-8871-4393e0b9c037)
    
- [<span data-ttu-id="29f28-159">Búsqueda híbrida</span><span class="sxs-lookup"><span data-stu-id="29f28-159">Hybrid search</span></span>](https://technet.microsoft.com/library/dn720906%28v=office.16%29.aspx)
    
- [<span data-ttu-id="29f28-160">Perfiles híbridos</span><span class="sxs-lookup"><span data-stu-id="29f28-160">Hybrid profiles</span></span>](https://support.office.com/article/Plan-hybrid-profiles-96d1eaf0-94eb-40c5-ab76-c82907777db4)
    
- [<span data-ttu-id="29f28-161">Selector de híbrido</span><span class="sxs-lookup"><span data-stu-id="29f28-161">Hybrid Picker</span></span>](https://support.office.com/article/Hybrid-picker-in-the-SharePoint-Online-admin-center-efce8417-c9bc-4a2c-ac9d-cce6c4e84a9c)
    
    <span data-ttu-id="29f28-162">Es fácil habilitar escenarios híbridos mediante asistentes que automatizan la configuración híbrida, disponible desde el Centro de administración de SharePoint Online en Office 365.</span><span class="sxs-lookup"><span data-stu-id="29f28-162">It is easy to enable hybrid scenarios using the wizards that automate hybrid configuration, available from the SharePoint Online admin center in Office 365.</span></span>
    
- [<span data-ttu-id="29f28-163">Iniciador de aplicaciones híbrido extensible</span><span class="sxs-lookup"><span data-stu-id="29f28-163">Extensible hybrid app launcher</span></span>](https://support.office.com/article/The-extensible-hybrid-app-launcher-617a7cb5-53da-4128-961a-64a840c0ab91)
    
    <span data-ttu-id="29f28-164">Permite a los usuarios ver y usar las aplicaciones y experiencias de Office 365 Video y Delve en las páginas de su granja de SharePoint local.</span><span class="sxs-lookup"><span data-stu-id="29f28-164">Allows users to view and use Office 365 video and Delve apps and experiences within the pages of their on-premises SharePoint farm.</span></span>
    
<span data-ttu-id="29f28-165">Todos estos escenarios híbridos de SharePoint, excepto el iniciador de aplicaciones híbrido extensible, están disponibles para los usuarios de SharePoint 2016 y SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="29f28-165">All of these SharePoint hybrid scenarios, except the Extensible hybrid app launcher, are available for both SharePoint 2016 and SharePoint 2013 users.</span></span>
  
<span data-ttu-id="29f28-166">Para obtener más información, vea [Implementación híbrida de SharePoint](http://hybrid.office.com/sharepoint/).</span><span class="sxs-lookup"><span data-stu-id="29f28-166">For more information, see [SharePoint Hybrid](http://hybrid.office.com/sharepoint/).</span></span>
  
## <a name="exchange-server-2016-hybrid"></a><span data-ttu-id="29f28-167">Exchange Server 2016 híbrido</span><span class="sxs-lookup"><span data-stu-id="29f28-167">Exchange Server 2016 Hybrid</span></span>

<span data-ttu-id="29f28-168">Con Exchange Server 2016 híbrido, puede materializar los beneficios de Exchange Online en Office 365 para los usuarios en línea mientras los usuarios locales siguen usando la infraestructura existente de Exchange Server. </span><span class="sxs-lookup"><span data-stu-id="29f28-168">With Exchange Server 2016 Hybrid, you can realize the benefits of Exchange Online in Office 365 for online users while on-premises users continue to use existing Exchange Server infrastructure.</span></span> 
  
<span data-ttu-id="29f28-169">**Figura 5: La configuración híbrida de Exchange 2016**</span><span class="sxs-lookup"><span data-stu-id="29f28-169">**Figure 5: The Exchange 2016 hybrid configuration**</span></span>

![La configuración híbrida de Exchange 2016](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-EX.png)
  
<span data-ttu-id="29f28-171">La figura 5 muestra la configuración híbrida de Exchange 2016, formado por los servidores de buzón de correo de Exchange locales comunicarse con Exchange Online Protection y buzones de correo en Office 365.</span><span class="sxs-lookup"><span data-stu-id="29f28-171">Figure 5 shows the Exchange 2016 hybrid configuration, consisting of on-premises Exchange mailbox servers communicating with Exchange Online Protection and mailboxes in Office 365.</span></span>
  
<span data-ttu-id="29f28-172">Algunos usuarios tienen un servidor de correo local y otros usan Exchange Online, pero todos comparten el mismo espacio de direcciones de correo. </span><span class="sxs-lookup"><span data-stu-id="29f28-172">Some users have an on-premises email server and some users use Exchange Online, but all users share the same e-mail address space.</span></span> 
  
<span data-ttu-id="29f28-173">Esta configuración híbrida:</span><span class="sxs-lookup"><span data-stu-id="29f28-173">This hybrid configuration:</span></span>
  
- <span data-ttu-id="29f28-174">Aprovecha la infraestructura existente de Exchange Server durante la migración a Exchange Online con el tiempo, según su programación.


</span><span class="sxs-lookup"><span data-stu-id="29f28-174">Leverages your existing Exchange Server infrastructure while you migrate to Exchange Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="29f28-175">Permite admitir sitios remotos sin invertir en infraestructura de sucursales.</span><span class="sxs-lookup"><span data-stu-id="29f28-175">Allows you to support remote sites without investing in branch office infrastructure.</span></span>
    
- <span data-ttu-id="29f28-176">Permite enrutar el correo electrónico entrante de Internet a través de Exchange Online Protection en Office 365.</span><span class="sxs-lookup"><span data-stu-id="29f28-176">Allows you to route incoming Internet email through Exchange Online Protection in Office 365.</span></span>
    
- <span data-ttu-id="29f28-177">Satisface las necesidades de organizaciones multinacionales con subsidiarias que necesitan que los datos residan localmente.</span><span class="sxs-lookup"><span data-stu-id="29f28-177">Serves the needs of multinational organizations with subsidiaries that require data to reside on-premises.</span></span>
    
<span data-ttu-id="29f28-178">También puede integrar esta configuración híbrida con otras aplicaciones de Microsoft Office 365, como Skype Empresarial Online y SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="29f28-178">You can also integrate this hybrid configuration with other Microsoft Office 365 applications, including Skype for Business Online and SharePoint Online.</span></span>
  
<span data-ttu-id="29f28-179">Para obtener más información, vea [Implementación híbrida de Exchange](http://hybrid.office.com/exchange/)y de [Las implementaciones híbridas de Exchange Server](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx) .</span><span class="sxs-lookup"><span data-stu-id="29f28-179">For more information, see [Exchange Server Hybrid Deployments](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx) and [Exchange Hybrid](http://hybrid.office.com/exchange/).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="29f28-180">Vea también</span><span class="sxs-lookup"><span data-stu-id="29f28-180">See Also</span></span>

[<span data-ttu-id="29f28-181">Microsoft Hybrid Cloud para arquitectos profesionales</span><span class="sxs-lookup"><span data-stu-id="29f28-181">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="29f28-182">Recursos de arquitectura de TI de la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="29f28-182">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="29f28-183">Mapa de ruta de Enterprise Cloud de Microsoft: Recursos para los responsables de decisiones de TI</span><span class="sxs-lookup"><span data-stu-id="29f28-183">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



