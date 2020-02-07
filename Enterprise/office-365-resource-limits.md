---
title: Office 365 límites de recursos
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: 'Resumen: información acerca de los límites de recursos para las distintas aplicaciones de Office 365.'
ms.openlocfilehash: 112d910ae724ad01629aaef5a8e2e1756ceb8ecf
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844321"
---
# <a name="resource-limits"></a><span data-ttu-id="5e7e4-103">Límites de recursos</span><span class="sxs-lookup"><span data-stu-id="5e7e4-103">Resource Limits</span></span>

<span data-ttu-id="5e7e4-104">Los límites de recursos se aplican mediante cuotas (límites) y limitación.</span><span class="sxs-lookup"><span data-stu-id="5e7e4-104">Resource limits are enforced using quotas (limits) and throttling.</span></span> <span data-ttu-id="5e7e4-105">Azure Active Directory y los servicios individuales de Office 365 usan ambos.</span><span class="sxs-lookup"><span data-stu-id="5e7e4-105">Azure Active Directory and the individual Office 365 services use both.</span></span> <span data-ttu-id="5e7e4-106">Los límites son específicos del servicio y cambian a lo largo del tiempo a medida que se agregan nuevas capacidades.</span><span class="sxs-lookup"><span data-stu-id="5e7e4-106">Limits are service-specific and change over time as new capabilities are added.</span></span> <span data-ttu-id="5e7e4-107">Para obtener más información sobre los límites actuales para los distintos servicios, vea los siguientes temas:</span><span class="sxs-lookup"><span data-stu-id="5e7e4-107">For details on the current limits for the various services, see the following topics:</span></span>

- [<span data-ttu-id="5e7e4-108">Límites y restricciones del servicio Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="5e7e4-108">Azure Active Directory service limits and restrictions</span></span>](https://msdn.microsoft.com/library/azure/dn764971.aspx)
- [<span data-ttu-id="5e7e4-109">Límites de Exchange Online</span><span class="sxs-lookup"><span data-stu-id="5e7e4-109">Exchange Online Limits</span></span>](https://technet.microsoft.com/library/exchange-online-limits.aspx)
- [<span data-ttu-id="5e7e4-110">Límites de Exchange Online Protection</span><span class="sxs-lookup"><span data-stu-id="5e7e4-110">Exchange Online Protection Limits</span></span>](https://technet.microsoft.com/library/exchange-online-protection-limits.aspx)
- [<span data-ttu-id="5e7e4-111">Límites y límites del software de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5e7e4-111">SharePoint Online software boundaries and limits</span></span>](https://support.office.com/article/SharePoint-Online-software-boundaries-and-limits-8F34FF47-B749-408B-ABC0-B605E1F6D498)
- [<span data-ttu-id="5e7e4-112">Límites de Skype empresarial</span><span class="sxs-lookup"><span data-stu-id="5e7e4-112">Skype for Business Limits</span></span>](https://technet.microsoft.com/library/skype-for-business-online-limits.aspx)
- [<span data-ttu-id="5e7e4-113">Límites de frecuencia y API de REST de Yammer</span><span class="sxs-lookup"><span data-stu-id="5e7e4-113">Yammer REST API and Rate Limits</span></span>](https://developer.yammer.com/docs/rest-api-rate-limits)
- [<span data-ttu-id="5e7e4-114">Límites de tamaño de archivo en Sway</span><span class="sxs-lookup"><span data-stu-id="5e7e4-114">File Size Limits in Sway</span></span>](https://support.office.com/article/File-size-limits-in-Sway-4db21bc6-b42b-499f-9272-66e089db109f)

<span data-ttu-id="5e7e4-115">Además de estos límites, se usan varios mecanismos de limitación a través de Azure Active Directory y Office 365.</span><span class="sxs-lookup"><span data-stu-id="5e7e4-115">In addition to these limits, several throttling mechanisms are used throughout Azure Active Directory and Office 365.</span></span> <span data-ttu-id="5e7e4-116">La limitación en el servicio es especialmente importante, dado que los recursos de red en los centros de recursos de Microsoft están optimizados para el amplio conjunto de clientes que usan los servicios.</span><span class="sxs-lookup"><span data-stu-id="5e7e4-116">Throttling within the service is especially important, given that network resources in Microsoft's datacenters are optimized for the broad set of customers that use the services.</span></span> <span data-ttu-id="5e7e4-117">Los mecanismos de limitación incluyen:</span><span class="sxs-lookup"><span data-stu-id="5e7e4-117">Throttling mechanisms include:</span></span>

- <span data-ttu-id="5e7e4-118">Azure Active Directory y Office 365 característica de limitación a nivel de usuario, que limitan el número de transacciones o llamadas simultáneas (por script o código) que un solo usuario puede realizar.</span><span class="sxs-lookup"><span data-stu-id="5e7e4-118">Azure Active Directory and Office 365 feature user-level throttling, which limit the number of transactions or concurrent calls (by script or code) that can be performed by a single user.</span></span>
- <span data-ttu-id="5e7e4-119">Se asigna una directiva de limitación de PowerShell predeterminada a cada inquilino en la creación del espacio empresarial.</span><span class="sxs-lookup"><span data-stu-id="5e7e4-119">A default PowerShell throttling policy is assigned to each tenant at tenant creation.</span></span> <span data-ttu-id="5e7e4-120">Esta configuración afecta a otros elementos, como el número máximo de sesiones simultáneas de PowerShell que puede abrir un administrador único.</span><span class="sxs-lookup"><span data-stu-id="5e7e4-120">These settings affect other items, such as the maximum number of simultaneous PowerShell sessions that can be opened by a single administrator.</span></span>
- <span data-ttu-id="5e7e4-121">Cada cliente de Exchange Online tiene una directiva de servicios web Exchange (EWS) predeterminada que se ajusta a las operaciones de cliente de EWS y que se aplica a todos los clientes de Outlook.</span><span class="sxs-lookup"><span data-stu-id="5e7e4-121">Each Exchange Online customer has a default Exchange Web Services (EWS) policy that is tuned for EWS client operations, and throttling that applies to all Outlook clients.</span></span>
