---
title: Supervisar la conectividad de Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/6/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 53cdb60c-a6b2-4848-b3ff-e7b75dc3fd1f
description: 'Una vez que haya implementado Office 365, puede mantener la conectividad de Office 365 mediante algunas de las siguientes herramientas y técnicas. Es conveniente que conozca las instrucciones oficiales de Continuidad y estado del servicio, así como los Procedimientos recomendados para usar Office 365 en una red lenta. También es conveniente que use la aplicación Administrador de Office 365 y que agregue a marcadores Office 365 para empresas: ayuda para administradores.'
ms.openlocfilehash: 93fbc9448ce25ef3d5d3f1d577c6d1c23ae4472a
ms.sourcegitcommit: 226989f5a6a252e67debf7613bf13aa679a43f92
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2020
ms.locfileid: "41721971"
---
# <a name="monitor-office-365-connectivity"></a><span data-ttu-id="e3ec6-105">Supervisar la conectividad de Office 365</span><span class="sxs-lookup"><span data-stu-id="e3ec6-105">Monitor Office 365 connectivity</span></span>

<span data-ttu-id="e3ec6-p102">Una vez que haya implementado Office 365, puede mantener la conectividad de Office 365 mediante algunas de las siguientes herramientas y técnicas. Es conveniente que conozca las instrucciones oficiales de [Continuidad y estado del servicio](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity), así como los [Procedimientos recomendados para usar Office 365 en una red lenta](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166). También es conveniente que use la [aplicación Administración de Office 365](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/) y que agregue a marcadores [Office 365 para empresas: ayuda para administradores](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791).</span><span class="sxs-lookup"><span data-stu-id="e3ec6-p102">Once you've deployed Office 365, you can maintain Office 365 connectivity using some of the tools and techniques below. You'll want to understand the official [Service Health and Continuity](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity) guidelines as well as our [Best practices for using Office 365 on a slow network](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166). You'll also want to grab the [Office 365 admin app](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/) and bookmark our [Office 365 for business - Admin Help](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791).</span></span>
  
## <a name="monitoring-office-365-connectivity"></a><span data-ttu-id="e3ec6-109">Supervisar la conectividad de Office 365</span><span class="sxs-lookup"><span data-stu-id="e3ec6-109">Monitoring Office 365 Connectivity</span></span>

|||
|:-----|:-----|
|<span data-ttu-id="e3ec6-110">**Recibir notificaciones de los nuevos puntos de conexión de Office 365**</span><span class="sxs-lookup"><span data-stu-id="e3ec6-110">**Getting notified of new Office 365 endpoints**</span></span> <br/> |<span data-ttu-id="e3ec6-p103">Si va a[Administrar los puntos de conexión de Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), es conveniente que reciba notificaciones cuando publiquemos nuevos puntos de conexión. Puede suscribirse a nuestra fuente RSS con su lector RSS favorito. Aquí puede ver cómo [suscribirse a través de Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416). También puede [recibir las actualizaciones de la fuente RSS por correo electrónico](https://go.microsoft.com/fwlink/p/?LinkId=532417).</span><span class="sxs-lookup"><span data-stu-id="e3ec6-p103">If you're [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), you'll want to receive notifications when we publish new endpoints, you can subscribe to our RSS feed using your favorite RSS reader. Here is how to [subscribe via Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) or you can [have the RSS feed updates emailed to you](https://go.microsoft.com/fwlink/p/?LinkId=532417).  </span></span><br/> |
|<span data-ttu-id="e3ec6-113">**Usar System Center para supervisar Office 365**</span><span class="sxs-lookup"><span data-stu-id="e3ec6-113">**Use System Center to Monitor Office 365**</span></span> <br/> |<span data-ttu-id="e3ec6-p104">Si va a usar Microsoft System Center, puede descargar el [módulo de administración de System Center para Office 365](https://www.microsoft.com/download/details.aspx?id=43708) para empezar a supervisar Office 365 hoy mismo. Para obtener instrucciones más detalladas, consulte la guía de operaciones del módulo de administración o la entrada de blog [Supervisión de Office 365 con System Center Operations Manager](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx).</span><span class="sxs-lookup"><span data-stu-id="e3ec6-p104">If you're using Microsoft System Center, you can download the [System Center Management Pack for Office 365](https://www.microsoft.com/download/details.aspx?id=43708) to begin monitoring Office 365 today. For more detailed guidance, please see the management pack operations guide or this blog post [Office365 Monitoring using System Centre Operations Manager](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx)</span></span> <br/> |
|<span data-ttu-id="e3ec6-116">**Supervisar el estado de Azure ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="e3ec6-116">**Monitoring the health of Azure ExpressRoute**</span></span> <br/> |<span data-ttu-id="e3ec6-117">Si va a conectarse a Office 365 con Azure ExpressRoute para Office 365, es conveniente que se asegure de usar tanto el Panel de estado del servicio de Office 365 como la [Reducción del tiempo de solución de problemas con Azure Resource Health](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/) de Azure.</span><span class="sxs-lookup"><span data-stu-id="e3ec6-117">If you are connecting to Office 365 using Azure ExpressRoute for Office 365, you'll want to ensure that you're using both the Office 365 Service Health Dashboard as well as the Azure [Reducing troubleshooting time with Azure Resource health](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/)</span></span> <br/> |
|<span data-ttu-id="e3ec6-118">**Usar Azure AD Connect Health con AD FS**</span><span class="sxs-lookup"><span data-stu-id="e3ec6-118">**Using Azure AD Connect Health with AD FS**</span></span> <br/> |<span data-ttu-id="e3ec6-119">Si va a usar AD FS para el inicio de sesión único con Office 365, es conveniente que empiece a [usar Azure AD Connect Health para supervisar su infraestructura de AD FS](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/).</span><span class="sxs-lookup"><span data-stu-id="e3ec6-119">If you're using AD FS for Single Sign-On with Office 365, you'll want to begin [using Azure AD Connect Health to monitor your AD FS infrastructure](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/).</span></span>  <br/> |
|<span data-ttu-id="e3ec6-120">**Supervisar Office 365 mediante programación**</span><span class="sxs-lookup"><span data-stu-id="e3ec6-120">**Programmatically monitor Office 365**</span></span> <br/> |<span data-ttu-id="e3ec6-121">Consulte nuestra guía sobre la [API de administración de Office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview).</span><span class="sxs-lookup"><span data-stu-id="e3ec6-121">Refer to our guidance on the [Office 365 Management API](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview).</span></span>  <br/> |

<span data-ttu-id="e3ec6-122">Este es un vínculo breve que se puede usar para volver: [https://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)</span><span class="sxs-lookup"><span data-stu-id="e3ec6-122">Here's a short link you can use to come back: [https://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e3ec6-123">Vea también</span><span class="sxs-lookup"><span data-stu-id="e3ec6-123">See also</span></span>

[<span data-ttu-id="e3ec6-124">Configuración de los servicios y las aplicaciones de Office 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="e3ec6-124">Configure Office 365 Enterprise services and applications</span></span>](configure-services-and-applications.md)
  
[<span data-ttu-id="e3ec6-125">Preparar la organización para Office 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="e3ec6-125">Get your organization ready for Office 365 Enterprise</span></span>](get-your-organization-ready-for-office-365.md)
  
[<span data-ttu-id="e3ec6-126">Planeamiento de red y ajuste del rendimiento para Office 365</span><span class="sxs-lookup"><span data-stu-id="e3ec6-126">Network planning and performance tuning for Office 365</span></span>](network-planning-and-performance.md)
  
[<span data-ttu-id="e3ec6-127">Integración de Office 365 con entornos locales</span><span class="sxs-lookup"><span data-stu-id="e3ec6-127">Office 365 integration with on-premises environments</span></span>](office-365-integration.md)
  
[<span data-ttu-id="e3ec6-128">Administrar puntos de conexión de Office 365</span><span class="sxs-lookup"><span data-stu-id="e3ec6-128">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
