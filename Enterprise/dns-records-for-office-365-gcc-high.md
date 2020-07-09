---
title: Registros DNS para Office 365 GCC High
ms.author: dzazzo
author: dzazzo
manager: dzazzo
ms.date: 05/19/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- OGA150
- OGC150
- OGD150
- MOE150
ms.assetid: ''
description: 'Resumen: registros DNS para Office 365 GCC High'
hideEdit: true
ms.openlocfilehash: 9bcaa71ab965f01481887d50a3e6ddbbbe3fadee
ms.sourcegitcommit: 576c3dbdef535f952a861197dea5348908da9504
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "44339807"
---
# <a name="dns-records-for-office-365-gcc-high"></a>Registros DNS para Office 365 GCC High

*Este artículo se aplica a Office 365 GCC High y Microsoft 365 GCC High*

Como parte de la incorporación a Office 365 GCC High, tendrá que agregar los dominios SMTP y SIP a su inquilino de servicios en línea.  Para hacerlo, use el cmdlet New-MsolDomain en Azure AD PowerShell o use el [portal de Azure Government](https://portal.azure.us) para iniciar el proceso de agregar el dominio y demostrar la propiedad.

Una vez que haya agregado los dominios al espacio empresarial y se hayan validado, use las siguientes instrucciones para agregar los registros DNS adecuados para los servicios que se indican a continuación.  Es posible que deba modificar la tabla que se muestra a continuación para ajustarse a las necesidades de su organización con respecto a los registros MX de entrada y los registros de Exchange Autodiscover existentes que haya en marcha.  Recomendamos encarecidamente coordinar estos registros DNS con su equipo de mensajería para evitar interrupciones o entregas no deseadas de correo electrónico.

## <a name="exchange-online"></a>Exchange en línea

| Tipo | Prioridad | Nombre de host | Apunta a una dirección o un valor | TTL |
| --- | --- | --- | --- | --- |
| MX | comprendi | @ | *tenant*. mail.Protection.Office365.US (consulte a continuación para obtener más información) | 1 Hour |
| TXT | - | @ | v = spf1 include include SPF. Protection. Office365. US-All | 1 Hour |
| CNAME | - | autodiscover | autodiscover.office365.us | 1 Hour |

### <a name="exchange-autodiscover-record"></a>Registro de detección automática de Exchange

Si tiene Exchange Server local, le recomendamos dejar el registro existente en su lugar mientras migra a Exchange Online y actualizar dicho registro una vez que haya completado la migración. 

### <a name="exchange-online-mx-record"></a>Registro MX de Exchange Online

El valor del registro MX para los dominios aceptados sigue un formato estándar, como se ha indicado anteriormente: *tenant*. mail.Protection.Office365.US, reemplazando a *tenant* con la primera parte del nombre del espacio empresarial predeterminado.

Por ejemplo, si el nombre de su espacio empresarial es contoso.onmicrosoft.us, usaría **contoso.mail.Protection.Office365.US** como el valor para el registro MX.

## <a name="skype-for-business-online"></a>Skype Empresarial Online

### <a name="cname-records"></a>Registros CNAME

| Tipo | Nombre de host | Apunta a una dirección o un valor | TTL |
| --- | --- | --- | --- |
| CNAME | sip | sipdir.online.gov.skypeforbusiness.us | 1 Hour |
| CNAME | lyncdiscover | webdir.online.gov.skypeforbusiness.us | 1 Hour |

### <a name="srv-records"></a>Registros SRV

| Tipo | Servicio | Protocolo | Puerto | Peso | Priority | Nombre | Target | TTL |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| SRV | \_sip | \_MTLS | 443 | 1  | 100 | @ | sipdir.online.gov.skypeforbusiness.us | 1 hora |
| SRV | \_sipfederationtls | \_TPC | 5061 | 1  | 100 | @ | sipfed.online.gov.skypeforbusiness.us | 1 Hour |

## <a name="additional-dns-records"></a>Registros DNS adicionales

> [!IMPORTANT]
> Si ya tiene un registro CNAME de *msoid* en la zona DNS, debe **quitar** el registro de DNS en este momento.  El registro msoid es incompatible con las aplicaciones empresariales de Microsoft 365 *(anteriormente Office 365 ProPlus)* y evitará que la activación se realice correctamente.
