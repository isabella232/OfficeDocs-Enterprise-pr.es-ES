---
title: Supervisión de la conectividad de Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 8/4/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 53cdb60c-a6b2-4848-b3ff-e7b75dc3fd1f
description: Una vez que haya implementado Microsoft 365, puede mantener la conectividad de Microsoft 365 con algunas de las herramientas y técnicas que se describen a continuación. Querrá comprender las directrices oficiales de estado y continuidad del servicio, así como los procedimientos recomendados para usar Microsoft 365 en una red lenta.
ms.openlocfilehash: aa47ff76f70e48285c6ca5f21ffdf30f1db52521
ms.sourcegitcommit: a9021ba0800ffc0da21cf2c4da67ab1da2d97099
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2020
ms.locfileid: "46571013"
---
# <a name="monitor-microsoft-365-connectivity"></a>Supervisión de la conectividad de Microsoft 365

Una vez que haya implementado Microsoft 365, puede mantener la conectividad de Microsoft 365 con algunas de las herramientas y técnicas que se describen a continuación. Querrá comprender las directrices oficiales de [Estado y continuidad del servicio](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity) , así como los [procedimientos recomendados para usar Microsoft 365 en una red lenta](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166). También querrá captar la aplicación de [Administración de microsoft 365](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/) y marcar nuestra [ayuda de administración de Microsoft 365 para empresas](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791).
  
## <a name="monitoring-microsoft-365-connectivity"></a>Supervisión de la conectividad de Microsoft 365

|||
|:-----|:-----|
|**Recibir notificaciones de los nuevos puntos de conexión de 365 de Microsoft** <br/> |Si está [administrando los puntos de conexión de 365 de Microsoft](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), querrá recibir notificaciones cuando publiquemos nuevos puntos de conexión, puede suscribirse a nuestra fuente RSS con su lector RSS favorito. Aquí le mostramos cómo [suscribirse a través de Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) o puede hacer que [la fuente RSS se actualice por correo electrónico](https://go.microsoft.com/fwlink/p/?LinkId=532417).  <br/> |
|**Usar System Center para supervisar Microsoft 365** <br/> |Si está usando Microsoft System Center, puede descargar el [módulo de administración de System Center para Office 365](https://www.microsoft.com/download/details.aspx?id=43708) para empezar a supervisar Microsoft 365 hoy. Para obtener instrucciones más detalladas, consulte la guía de operaciones del módulo de administración o esta entrada de blog [supervisión de Office365 mediante el centro de operaciones de System Centre](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx) <br/> |
|**Supervisar el estado de Azure ExpressRoute** <br/> |Si se va a conectar a Microsoft 365 mediante Azure ExpressRoute para Microsoft 365, querrá asegurarse de que está usando tanto el panel de estado del servicio de Microsoft 365 como el tiempo de solución de problemas de la reducción de Azure [con Azure Resource Health](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/) <br/> |
|**Usar Azure AD Connect Health con AD FS** <br/> |Si está usando AD FS para el inicio de sesión único con Microsoft 365, querrá empezar a [usar Azure ad Connect Health para supervisar su infraestructura de AD FS](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/).  <br/> |
|**Supervisión mediante programación de Microsoft 365** <br/> |Consulte nuestras instrucciones en la [API de administración de 365 de Microsoft](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview).  <br/> |

Este es un vínculo breve que se puede usar para volver: [https://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)
  
## <a name="see-also"></a>Vea también

[Configuración de Microsoft 365 Enterprise Services y aplicaciones](configure-services-and-applications.md)
  
[Preparar a su organización para Microsoft 365 Enterprise](get-your-organization-ready-for-office-365.md)
  
[Planeamiento de red y ajuste del rendimiento para Microsoft 365](network-planning-and-performance.md)
  
[Integración de Microsoft 365 con entornos locales](office-365-integration.md)
  
[Administración de puntos de conexión de 365 de Microsoft](managing-office-365-endpoints.md)
