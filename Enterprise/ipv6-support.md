---
title: Compatibilidad con IPv6 en servicios de Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/10/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c08786fb-298e-437c-8222-dab7625fc815
description: 'Resumen: Describe la compatibilidad de IPv6 en los componentes de Microsoft Office 365 y en las ofertas de gobierno de Office 365.'
ms.openlocfilehash: 82af5c7659b3c16c8e92b45b65b6868a404eca23
ms.sourcegitcommit: c5ee713709d76f519cb77de0e12c435d8409f571
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2019
ms.locfileid: "28327362"
---
# <a name="ipv6-support-in-office-365-services"></a><span data-ttu-id="0a152-103">Compatibilidad con IPv6 en servicios de Office 365</span><span class="sxs-lookup"><span data-stu-id="0a152-103">IPv6 support in Office 365 services</span></span>

 <span data-ttu-id="0a152-104">**Resumen**: describe la compatibilidad de IPv6 en los componentes de Microsoft Office 365 y en las ofertas de gobierno de Office 365.</span><span class="sxs-lookup"><span data-stu-id="0a152-104">**Summary**: Describes IPv6 support in Microsoft Office 365 components and in Office 365 government offerings.</span></span>
  
<span data-ttu-id="0a152-p101">Office 365 es compatible con IPv6 y IPv4; Sin embargo, no todas las características de Office 365 totalmente se habilitan con IPv6. Esto significa que debe usar IPv4 e IPv6 para conectarse a Office 365. Si se van a filtrar el tráfico saliente a Office 365, la lista completa de las direcciones IPv6 que son compatibles con Office 365 puede encontrarse en el artículo de [las direcciones URL de Office 365 y los intervalos de direcciones IP](urls-and-ip-address-ranges.md). Después de la red está configurada y se permiten las direcciones IPv6 adecuadas, puede descargar el [plan de pruebas de IPv6 de Office 365](https://go.microsoft.com/fwlink/?LinkId=293447) desde Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="0a152-p101">Office 365 supports both IPv6 and IPv4; however, not all Office 365 features are fully enabled with IPv6. This means that you must use both IPv4 and IPv6 to connect to Office 365. If you are filtering your outbound traffic to Office 365, the full list of IPv6 addresses that are supported by Office 365 can be found in the article [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md). After your network is configured and the appropriate IPv6 addresses are allowed, you can download the [Office 365 IPv6 test plan](https://go.microsoft.com/fwlink/?LinkId=293447) from the Microsoft Download Center.</span></span>
  
||
|:-----|
| <span data-ttu-id="0a152-109">En este artículo forma parte de la [planeación de la red y ajuste del rendimiento de Office 365](https://aka.ms/tune).</span><span class="sxs-lookup"><span data-stu-id="0a152-109">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

## <a name="ipv6-support-in-office-365-subscription-service"></a><span data-ttu-id="0a152-110">Compatibilidad con IPv6 en el servicio de suscripción de Office 365</span><span class="sxs-lookup"><span data-stu-id="0a152-110">IPv6 support in Office 365 subscription service</span></span>

### <a name="exchange-online-and-ipv6"></a><span data-ttu-id="0a152-111">Exchange Online e IPv6</span><span class="sxs-lookup"><span data-stu-id="0a152-111">Exchange Online and IPv6</span></span>

<span data-ttu-id="0a152-p102">Si el programa que use para conectarse a Exchange Online admite IPv6, usará IPv6 de forma predeterminada en redes por cable e inalámbricas. Si desea controlar las comunicaciones a Exchange Online, use los intervalos de direcciones IP en [las direcciones URL de Office 365 y los intervalos de direcciones IP](urls-and-ip-address-ranges.md).</span><span class="sxs-lookup"><span data-stu-id="0a152-p102">If the program that you use to connect to Exchange Online supports IPv6, it will use IPv6 by default on both wired and wireless networks. If you want to control communications to Exchange Online, use the IP address ranges in [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="sharepoint-online-and-ipv6"></a><span data-ttu-id="0a152-114">SharePoint Online e IPv6</span><span class="sxs-lookup"><span data-stu-id="0a152-114">SharePoint Online and IPv6</span></span>

 <span data-ttu-id="0a152-115">**Office 365 gobierno G1/G3/G4/K1** Si el programa que use para conectarse a SharePoint Online admite IPv6, intentará usar IPv6 de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="0a152-115">**Office 365 Government G1/G3/G4/K1** If the program that you use to connect to SharePoint Online supports IPv6, it will attempt to use IPv6 by default.</span></span>
  
 <span data-ttu-id="0a152-p103">**Nube pública de varios inquilino** Microsoft habilita IPv6 en línea de SharePoint en su solicitud. Es necesario que proporcione que la CIDR expresa las direcciones IP para la infraestructura DNS de su organización. Tenga en cuenta que no se puede compartir esta infraestructura DNS por otras organizaciones para IPv6 a habilitarse para el inquilino. Después de habilitar IPv6, si el programa que use para conectarse a SharePoint Online admite IPv6, usa IPv6 de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="0a152-p103">**Public multi-tenant cloud** Microsoft enables SharePoint Online IPv6 at your request. You need to provide the CIDR notated IP addresses for your organization's DNS infrastructure. Keep in mind that this DNS infrastructure can't be shared by other organizations for IPv6 to be enabled for your tenant. After IPv6 is enabled, if the program that you use to connect to SharePoint Online supports IPv6, it uses IPv6 by default.</span></span>
  
<span data-ttu-id="0a152-p104">Si el programa que use para conectarse a SharePoint Online admite IPv6, usará IPv6 de forma predeterminada en redes por cable e inalámbricas. Si desea controlar las comunicaciones a SharePoint Online, use los intervalos de direcciones IP en [las direcciones URL de Office 365 y los intervalos de direcciones IP](urls-and-ip-address-ranges.md).</span><span class="sxs-lookup"><span data-stu-id="0a152-p104">If the program that you use to connect to SharePoint Online supports IPv6, it will use IPv6 by default on both wired and wireless networks. If you want to control communications to SharePoint Online, use the IP address ranges in [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span>
  
 <span data-ttu-id="0a152-122">**Office 365 gobierno G1/G3/G4/K1** Si el programa que use para conectarse a SharePoint Online admite IPv6, intentará usar IPv6 de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="0a152-122">**Office 365 Government G1/G3/G4/K1** If the program that you use to connect to SharePoint Online supports IPv6, it will attempt to use IPv6 by default.</span></span>
  
### <a name="skype-for-business-and-ipv6"></a><span data-ttu-id="0a152-123">Skype para empresas y IPv6</span><span class="sxs-lookup"><span data-stu-id="0a152-123">Skype for Business and IPv6</span></span>

<span data-ttu-id="0a152-124">Por favor, tenga en cuenta IPv6 no es compatible con Skype para la empresa y ya no se puede habilitar.</span><span class="sxs-lookup"><span data-stu-id="0a152-124">Please be aware IPv6 is not supported in Skype for Business and can no longer be enabled.</span></span>
  
### <a name="exchange-online-protection-and-ipv6"></a><span data-ttu-id="0a152-125">Protección en línea de Exchange e IPv6</span><span class="sxs-lookup"><span data-stu-id="0a152-125">Exchange Online Protection and IPv6</span></span>

<span data-ttu-id="0a152-p105">Exchange Online Protection (EOP) es compatible con IPv6, si se produce la transmisión a través del protocolo de seguridad de capa de transporte. El intervalo de elevación de privilegios, use [las direcciones URL de Office 365 y los intervalos de direcciones IP](urls-and-ip-address-ranges.md).</span><span class="sxs-lookup"><span data-stu-id="0a152-p105">Exchange Online Protection (EOP) supports IPv6 if the transmission occurs over Transport Layer Security Protocol. For the EOP range, use [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="ipv6-support-for-office-365-government-offerings"></a><span data-ttu-id="0a152-128">Compatibilidad con IPv6 para las ofertas de Office 365 Administración pública</span><span class="sxs-lookup"><span data-stu-id="0a152-128">IPv6 support for Office 365 government offerings</span></span>

<span data-ttu-id="0a152-p106">Compatibilidad con IPv6 de Office 365 para las ofertas de gobierno se ajusta a la oficina de administración y memorando Budget (OMB) para directores de información de departamentos ejecutivo y organismos, así como la Federal gobierno adopción de Internet Protocol versión 6 (IPv6 ) memorando. [Microsoft Office 365 para el gobierno](https://go.microsoft.com/fwlink/p/?LinkId=325414) es un servicio de varios inquilino que nos datos gubernamentales almacena en una nube de la Comunidad separadas. Al igual que otras ofertas de Office 365, proporciona servicios de productividad y colaboración, incluido Exchange Online, Skype para la empresa, SharePoint Online y Office Professional Plus.</span><span class="sxs-lookup"><span data-stu-id="0a152-p106">Office 365 IPv6 support for government offerings conforms to the Office of Management and Budget (OMB) Memorandum for Chief Information Officers of Executive Departments and Agencies, as well as the Federal Government Adoption of Internet Protocol Version 6 (IPv6) memorandum. [Microsoft Office 365 for Government](https://go.microsoft.com/fwlink/p/?LinkId=325414) is a multi-tenant service that stores US government data in a segregated community cloud. Like other Office 365 offerings, it provides productivity and collaboration services, including Exchange Online, Skype for Business, SharePoint Online, and Office Professional Plus.</span></span> 

<span data-ttu-id="0a152-p107">Las ofertas de administración pública de Microsoft Office 365 se aplican sólo para 2013 y versiones posteriores. Para obtener más información acerca de las ofertas de gobierno de Office 365, vea [anunciar Office 365 para el gobierno: A nosotros gobierno nube de la Comunidad](https://go.microsoft.com/fwlink/p/?LinkId=325414). El tráfico de internacional en las normativas de armas (ITAR) es un conjunto de reglamentaciones gubernamentales de Estados Unidos que controlan la exportación e importación de artículos relacionados con la defensa y servicios en la [Lista de municiones de Estados Unidos (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415).</span><span class="sxs-lookup"><span data-stu-id="0a152-p107">The Microsoft Office 365 government offerings apply only for 2013 and later. For more information about the Office 365 government offerings, see [Announcing Office 365 for Government: A US Government Community Cloud](https://go.microsoft.com/fwlink/p/?LinkId=325414). International Traffic in Arms Regulations (ITAR) is a set of US government regulations that control the export and import of defense-related articles and services on the [United States Munitions List (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415).</span></span> 

<span data-ttu-id="0a152-135">Microsoft Office 365 para empresas proporciona servicios de hospedaje dedicados para soluciones de productividad de Microsoft que admiten la seguridad, privacidad y los requisitos de cumplimiento de normativas para nosotros agencias federales que requieren Federal de información de seguridad Certificación de administración (FISMA) y entidades comerciales sujetas a ITAR.</span><span class="sxs-lookup"><span data-stu-id="0a152-135">Microsoft Office 365 for Enterprises provides dedicated hosting services for Microsoft productivity solutions that support the security, privacy, and regulatory compliance requirements for US federal agencies requiring Federal Information Security Management (FISMA) certification and commercial entities subject to ITAR.</span></span>
  
## <a name="things-to-consider-when-using-ipv6-and-office-365"></a><span data-ttu-id="0a152-136">Cosas que debe tener en cuenta cuando use IPv6 y Office 365</span><span class="sxs-lookup"><span data-stu-id="0a152-136">Things to consider when using IPv6 and Office 365</span></span>

<span data-ttu-id="0a152-p108">Se recomienda deshabilitar IPv6. Para obtener más información, vea este [artículo de instrucciones](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users). Para determinar qué versiones IP se usan en la red, tenga en cuenta lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="0a152-p108">We recommend that you do not disable IPv6. For more information, see this [guidance article](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users). To determine what IP versions are being used on your network, consider the following:</span></span>
  
- <span data-ttu-id="0a152-140">Si la presentación del comando **IPConfig** en el símbolo del sistema contiene filas con el nombre "Dirección IPv6" o "Dirección IPv6 temporal", que dispone de IPv6 en su entorno.</span><span class="sxs-lookup"><span data-stu-id="0a152-140">If the display of the **IPConfig** command at the command prompt contains rows named "IPv6 Address" or "Temporary IPv6 Address," you have IPv6 in your environment.</span></span>

- <span data-ttu-id="0a152-141">Si todas las direcciones IPv6 comienzan por "fe80" y se corresponden con las filas denominadas "Dirección IPv6 de vínculo Local", que no dispone de IPv6 en su entorno.</span><span class="sxs-lookup"><span data-stu-id="0a152-141">If all the IPv6 addresses begin with "fe80" and correspond to rows named "Link-Local IPv6 Address," you don't have IPv6 in your environment.</span></span>

<span data-ttu-id="0a152-142">Pueden que estas consideraciones se apliquen a su red:</span><span class="sxs-lookup"><span data-stu-id="0a152-142">These considerations might apply to your network:</span></span>
  
- <span data-ttu-id="0a152-p109">El servicio de suscripción pública no admite compras con tarjeta de crédito a través de IPv6. Esto no se aplica a la nube de comunidad de administración pública (GCC) porque la administración pública dispone de licencias de Contrato Enterprise (EA).</span><span class="sxs-lookup"><span data-stu-id="0a152-p109">The public subscription service does not support purchase by credit card over IPv6. This does not apply to the Government Community Cloud (GCC) because governments have Enterprise Agreement (EA) licensing.</span></span>

- <span data-ttu-id="0a152-145">IPv6 no admite algunos escenarios de Rights Management Services (RMS).</span><span class="sxs-lookup"><span data-stu-id="0a152-145">IPv6 does not support some Rights Management Services (RMS) scenarios.</span></span>

- <span data-ttu-id="0a152-146">IPv6 no admite BlackBerry® Enterprise Server (BES) porque BlackBerry no es compatible con IPv6.</span><span class="sxs-lookup"><span data-stu-id="0a152-146">IPv6 does not support BlackBerry® Enterprise Server (BES) because BlackBerry doesn't support IPv6.</span></span>

- <span data-ttu-id="0a152-p110">Si usa los servicios de federación de Active Directory (AD FS) con Office 365, anuncie su extremo de la red de AD FS a Office 365 usa IPv6 no se admite. No debe incluir registros AAAA en la entrada de DNS de AD FS al usar Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="0a152-p110">If you use Active Directory Federation Services (AD FS) with Office 365, advertising your AD FS network endpoint to Office 365 using IPv6 is not supported. You should not include AAAA records in the AD FS DNS entry when using Exchange Online.</span></span> 

<span data-ttu-id="0a152-149">Este es un vínculo breve que se puede usar para volver: [https://aka.ms/o365ip6](https://aka.ms/o365ip6)</span><span class="sxs-lookup"><span data-stu-id="0a152-149">Here's a short link you can use to come back: [https://aka.ms/o365ip6](https://aka.ms/o365ip6)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0a152-150">Vea también</span><span class="sxs-lookup"><span data-stu-id="0a152-150">See also</span></span>

<span data-ttu-id="0a152-151">[Ruta de aprendizaje de IPv6](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg250710(v%3dws.10))</span><span class="sxs-lookup"><span data-stu-id="0a152-151">[IPv6 Learning Roadmap](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg250710(v%3dws.10))</span></span>
  
[<span data-ttu-id="0a152-152">Guía de supervivencia de IPv6</span><span class="sxs-lookup"><span data-stu-id="0a152-152">IPv6 Survival Guide</span></span>](https://social.technet.microsoft.com/wiki/contents/articles/1728.ipv6-survival-guide.aspx)
