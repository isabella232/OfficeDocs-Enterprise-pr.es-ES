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
description: 'Resumen: información acerca de los límites de recursos para las distintas aplicaciones de Office 365.'
ms.openlocfilehash: 7ccbf2bdfe359dd44a0b03dcf6e2aed8d5daedbe
ms.sourcegitcommit: 9eb68633728cc78e9906dab222edbf9977b17e21
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2019
ms.locfileid: "38035490"
---
# <a name="resource-limits"></a>Límites de recursos

Los límites de recursos se aplican mediante cuotas (límites) y limitación. Azure Active Directory y los servicios individuales de Office 365 usan ambos. Los límites son específicos del servicio y cambian a lo largo del tiempo a medida que se agregan nuevas capacidades. Para obtener más información sobre los límites actuales para los distintos servicios, vea los siguientes temas:

- [Límites y restricciones del servicio Azure Active Directory](https://msdn.microsoft.com/library/azure/dn764971.aspx)
- [Límites de Exchange Online](https://technet.microsoft.com/library/exchange-online-limits.aspx)
- [Límites de Exchange Online Protection](https://technet.microsoft.com/library/exchange-online-protection-limits.aspx)
- [Límites y límites del software de SharePoint Online](https://support.office.com/article/SharePoint-Online-software-boundaries-and-limits-8F34FF47-B749-408B-ABC0-B605E1F6D498)
- [Límites de Skype empresarial](https://technet.microsoft.com/library/skype-for-business-online-limits.aspx)
- [Límites de frecuencia y API de REST de Yammer](https://developer.yammer.com/docs/rest-api-rate-limits)
- [Límites de tamaño de archivo en Sway](https://support.office.com/article/File-size-limits-in-Sway-4db21bc6-b42b-499f-9272-66e089db109f)

Además de estos límites, se usan varios mecanismos de limitación a través de Azure Active Directory y Office 365. La limitación en el servicio es especialmente importante, dado que los recursos de red en los centros de recursos de Microsoft están optimizados para el amplio conjunto de clientes que usan los servicios. Los mecanismos de limitación incluyen:

- Azure Active Directory y Office 365 característica de limitación a nivel de usuario, que limitan el número de transacciones o llamadas simultáneas (por script o código) que un solo usuario puede realizar.
- Se asigna una directiva de limitación de PowerShell predeterminada a cada inquilino en la creación del espacio empresarial. Esta configuración afecta a otros elementos, como el número máximo de sesiones simultáneas de PowerShell que puede abrir un administrador único.
- Cada cliente de Exchange Online tiene una directiva de servicios web Exchange (EWS) predeterminada que se ajusta a las operaciones de cliente de EWS y que se aplica a todos los clientes de Outlook.
