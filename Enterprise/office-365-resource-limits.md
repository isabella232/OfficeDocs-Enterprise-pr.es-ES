---
title: Límites de recursos de Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
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
description: En este artículo, puede encontrar información acerca de los límites de recursos para las distintas aplicaciones en Microsoft 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 4d2e7987620891ddeac2c4fa08aaeb203f001f57
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606306"
---
# <a name="resource-limits"></a>Límites de recursos

Los límites de recursos se aplican mediante cuotas (límites) y limitación. Azure Active Directory (Azure AD) y los servicios individuales de Microsoft 365 usan ambos. Los límites son específicos del servicio y cambian a lo largo del tiempo a medida que se agregan nuevas capacidades. Para obtener más información sobre los límites actuales para los distintos servicios, vea los siguientes temas:

- [Límites y restricciones del servicio de Azure AD](https://docs.microsoft.com/azure/azure-resource-manager/management/azure-subscription-service-limits)
- [Límites de Exchange Online](https://technet.microsoft.com/library/exchange-online-limits.aspx)
- [Límites de Exchange Online Protection](https://technet.microsoft.com/library/exchange-online-protection-limits.aspx)
- [Límites y límites del software de SharePoint Online](https://support.office.com/article/SharePoint-Online-software-boundaries-and-limits-8F34FF47-B749-408B-ABC0-B605E1F6D498)
- [Límites de Skype empresarial](https://technet.microsoft.com/library/skype-for-business-online-limits.aspx)
- [Límites de frecuencia y API de REST de Yammer](https://developer.yammer.com/docs/rest-api-rate-limits)
- [Límites de tamaño de archivo en Sway](https://support.office.com/article/File-size-limits-in-Sway-4db21bc6-b42b-499f-9272-66e089db109f)

Además de estos límites, se usan varios mecanismos de limitación en Azure AD y Microsoft 365. La limitación en el servicio es especialmente importante, dado que los recursos de red en los centros de recursos de Microsoft están optimizados para el amplio conjunto de clientes que usan los servicios. Los mecanismos de limitación incluyen:

- La limitación a nivel de usuario de la característica de Azure AD y Microsoft 365, que limita el número de transacciones o llamadas simultáneas (por script o código) que un solo usuario puede realizar.
- Se asigna una directiva de limitación de PowerShell predeterminada a cada inquilino en la creación del espacio empresarial. Esta configuración afecta a otros elementos, como el número máximo de sesiones simultáneas de PowerShell que puede abrir un administrador único.
- Cada cliente de Exchange Online tiene una directiva de servicios web Exchange (EWS) predeterminada que se ajusta a las operaciones de cliente de EWS y que se aplica a todos los clientes de Outlook.
